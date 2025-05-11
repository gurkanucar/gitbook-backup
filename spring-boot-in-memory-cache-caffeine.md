# Spring Boot In Memory Cache - Caffeine

title: "Spring Boot In Memory Cache - Caffeine"\
source: https://www.gurkanucar.com/spring-boot-in-memory-cache-caffeine/\
date: 2025-05-11 12:49\
tags:\
description:

[source](https://www.gurkanucar.com/spring-boot-in-memory-cache-caffeine/)

## Spring Boot In Memory Cache - Caffeine

By [gurkanucar](https://www.gurkanucar.com/author/gurkanucar/) --- 05 Apr 2025

![image](https://www.gurkanucar.com/content/images/2025/04/image-3.png)

Cache, en basit haliyle veriyi önbellekte saklayan ve tekrar ihtiyaç duyulduğunda, ek bir işlem gerektirmeden hızlıca bu önbellekten getiren bir mekanizmadır. Normal şartlarda bir veriye erişmek istediğimizde doğrudan veritabanına sorgu atarız. Ancak bu, özellikle yoğun erişimlerde, veritabanına sürekli sorgu atılmasına ve dolayısıyla performansın düşmesine neden olur.

> **Çok konuşma kodu ver diyenler için:** [**github**](https://github.com/gurkanucar/spring-boot-starter-template/tree/master/src/main/java/com/gucardev/springbootstartertemplate/infrastructure/config/cache?ref=gurkanucar.com)

Örneğin, uygulama ilk açıldığında çekilmesi gereken konfigürasyon verilerini sağlayan bir servisinizi düşünün. Bu servise çok sayıda kullanıcı aynı anda eriştiğinde veritabanına olan yük artar ve sistem performansı olumsuz etkilenir. Ancak bu tür, sık değişmeyen veriler için cache kullanmak, hem veritabanı yükünü azaltır hem de uygulama performansını ciddi ölçüde artırır.

Cache sistemleri kullanım senaryolarına göre farklı şekillerde uygulanabilir. En yaygın cache türleri şunlardır:

* **In-Memory Cache**
* **Disk Cache**
* **Browser Cache**
* **Database Cache**
* **Distributed Cache**

Spring Boot içerisinde cache işlemleri için farklı kütüphaneler kullanılabilir. En yaygın olanlar şunlardır:

* **Guava**
* **Caffeine**
* **Redis**

Bu yazıda, basit ve hafif bir çözüm olan **Caffeine Cache**'i ele alacağız.

‼️

**Ufak bir not:** Burada kullanılan yöntem, **birden fazla instance** şeklinde çalışan **uygulamalarda veri tutarsızlığ**ına sebep olabilir. Daha tutarlı bir cache mekanizması için redis ve türevleri gibi **distributed cache** kullanılması daha doğru olacaktır.

Eğer herhangi bir ek kütüphane tanımlamazsanız, Spring Boot varsayılan olarak `ConcurrentHashMap` kullanır. Ancak bu yapının **TTL (Time To Live)** gibi gelişmiş yapılandırma seçenekleri yoktur. Bu yüzden, TTL ve maksimum boyut gibi gelişmiş özellikler sunan **Caffeine** cache tercih edilmiştir.

İşe gerekli depencyleri eklemekle başlayalım:

```
            org.springframework.boot
            spring-boot-starter-cache
        
        
            com.github.ben-manes.caffeine
            caffeine
        
```

Cache i aktifleştirmek için `@EnableCaching` anotasyonu kullanmalıyız:

```
@EnableCaching
@SpringBootApplication
public class SpringBootStarterTemplateApplication {
    public static void main(String[] args) {
        SpringApplication.run(SpringBootStarterTemplateApplication.class, args);
    }
}
```

Cache'e ait logları daha iyi görebilmek adına `application.properties` dosyamıza aşağıdaki configurasyonu ekleyelim:

```
logging.level.org.springframework.cache=TRACE
```

Cache işlemleri için, metodlarin uzerine ekleyecegimiz bazı anotasyonlar vardır. Bunlar:

**@Cacheable:** Metodun sonuçlarını önbelleğe alır, aynı parametrelerle tekrar çağrıldığında metodu çalıştırmadan önbellekten sonuç döndürür.

**@CachePut:** Metodu her zaman çalıştırır ve sonucu önbelleğe kaydeder/günceller.

* **Not**: `@Cacheable`'dan farkı metodu atlamamasıdır, her zaman çalışır.

**@CacheEvict**: Önbellekteki verileri siler.

* **Not**: `allEntries` parametresi tüm önbellek verilerini siler

**Tüm Anotasyonlarda Ortak Parametreler**

* `value/cacheNames`: Önbellek adları
* `key`: Önbellek anahtarı için kullanılacak SpEL ifadesi
* `keyGenerator`: Özel anahtar üreteç sınıfı
* `cacheManager`: Kullanılacak önbellek yöneticisi
* `cacheResolver`: Önbellek çözümleyici
* `condition`: Önbellekleme koşulu
* `unless`: Önbellekleme yapılmayacak koşul

Aşağıda örnek kullanımını görebilirsiniz:

```
@Slf4j
@Service
@RequiredArgsConstructor
public class ProductService {
    private final ProductRepository productRepository;
    // Caches the result; skips DB call if data is in cache
    // key also can be like concat of => key = "'entity-' + #id"    
    @Cacheable(value = "products", key = "#id")
    public Product getProductById(Long id) {
        log.info("Fetching from DB...");
        return productRepository.findById(id).orElse(null);
    }
    // Always updates the DB and cache
    @CachePut(value = "products", key = "#product.id")
    public Product updateProduct(Product product) {
        log.info("Updating product and cache...");
        return productRepository.save(product);
    }
    // Deletes the product from DB and evicts the cache entry
    @CacheEvict(value = "products", key = "#id")
    public void deleteProduct(Long id) {
       log.info("Deleting from DB and cache...");
        productRepository.deleteById(id);
    }
    // clears entire cache
    @CacheEvict(value = "products", allEntries = true)
    public void clearAllCache() {
        log.info("All cache entries cleared.");
    }
}
```

**Not**: Eğer **aynı servis içerisinde `cache` kullanan bir methodu** çağırmanız gerekirse, direkt olarak metodu çağırdığınızda cache'in **çalışmadığını göreceksiniz**. Bu sorunu çözmek için **aşağıdaki yöntemi kullanabilirsiniz**:

```
import org.springframework.context.ApplicationContext;
...
public class MyClass {
  
  private final ApplicationContext applicationContext;
  private MyClass self() {
    return applicationContext.getBean(MyClass.class);
  }
  public void doSomethingWithCachedInSameClass(Long id) {
    // Use self-invocation to ensure @Cacheable is applied
    var existing = self().getById(id).orElseThrow(
        () -> new EntityNotFoundException("Entity not found"));
    log.info(existing.toString());
  }
 @Cacheable(key = "#id")
  public Optional getById(Long id) {
    return myEntityRepo.findById(id);
  }
```

Peki production ortaminda direkt bu halde mi kullanılıyor? Çoğunlukla hayır. Bunu daha yönetilebilir bir şekilde kullanmak gerek. Bu sepeble öncelikle bir `CacheNames` sınıfı oluşturalım ve kullanacağımız cache isimlerini ekleyelim:

```
public class CacheNames {
    public static final String PRODUCTS = "products";
    public static final String CACHE_USER_PREFERENCES = "user_preferences";
    public static final String CACHE_USER_SESSIONS = "user_sessions";
    public static final String CACHE_TEMPORARY_TOKENS = "temporary_tokens";
    public static List getAllCacheNames() {
        return Arrays.asList(PRODUCTS,
                CACHE_USER_PREFERENCES,
                CACHE_USER_SESSIONS,
                CACHE_TEMPORARY_TOKENS);
    }
}
```

Ardından bir cache managerı sınıfı oluşturalım:

```
cache.short.ttl=60
cache.medium.ttl=120
cache.default.max-size=1000
//@EnableCaching
@Configuration
public class CaffeineCacheConfig {
    // Cache Manager Bean Names
    public static final String CACHE_MANAGER_SHORT_LIVED = "shortLivedCacheManager";
    public static final String CACHE_MANAGER_MEDIUM_LIVED = "mediumLivedCacheManager";
    @Primary
    @Bean(CACHE_MANAGER_SHORT_LIVED)
    public CacheManager shortLivedCacheManager(
            @Value("${cache.short.ttl:60}") int shortTtlSeconds,
            @Value("${cache.default.max-size:1000}") int defaultMaxSize
    ) {
        return buildCacheManager(shortTtlSeconds, defaultMaxSize);
    }
    @Bean(CACHE_MANAGER_MEDIUM_LIVED)
    public CacheManager mediumLivedCacheManager(
            @Value("${cache.medium.ttl:120}") int mediumTtlSeconds,
            @Value("${cache.default.max-size:1000}") int defaultMaxSize
    ) {
        return buildCacheManager(mediumTtlSeconds, defaultMaxSize);
    }
    private CacheManager buildCacheManager(int ttlSeconds, int maxSize) {
        CaffeineCacheManager cacheManager = new CaffeineCacheManager();
        cacheManager.setCacheNames(CacheNames.getAllCacheNames());
        cacheManager.setCaffeine(
                Caffeine.newBuilder()
                        .expireAfterWrite(ttlSeconds, TimeUnit.SECONDS)
                        .maximumSize(maxSize)
        );
        return cacheManager;
    }
}
```

Burada iki farklı manager oluşturduk. Birisi uzun süren cache işlemeri diğeri ise kısa sürenler için. Ek olarak `@Primary` anotasyonu ile de, cache manager verilmeme durumunda default olarak kısa süreli cache manager ın seçilmesini ayarladık.

Aşağıda, cache in kullanıldığı daha kapsamlı bir örneği bulabilirsiniz:

```
@Service
@Slf4j
public class CacheDemoService {
    // Simulate database
    private final Map mockDatabase = new HashMap<>();
    /**
     * Basic caching example using short-lived cache (default)
     */
    @Cacheable(value = CacheNames.CACHE_PRODUCTS, key = "#id")
    public String getProductData(String id) {
        log.info("Cache MISS for product ID: {} - This would be a database call", id);
        simulateSlowOperation();
        return "Product data for " + id + " at " + System.currentTimeMillis();
    }
    /**
     * Caching example with medium-lived cache manager
     */
    @Cacheable(
            value = CacheNames.CACHE_USER_PREFERENCES,
            key = "#userId",
            cacheManager = CaffeineCacheConfig.CACHE_MANAGER_MEDIUM_LIVED
    )
    public String getUserPreferences(String userId) {
        log.info("Cache MISS for user preferences, userId: {} - This would be a database call", userId);
        simulateSlowOperation();
        return "User preferences for " + userId + " at " + System.currentTimeMillis();
    }
    /**
     * Cache update example using CachePut
     */
    @CachePut(value = CacheNames.CACHE_USER_SESSIONS, key = "#sessionId")
    public String updateSession(String sessionId, String data) {
        log.info("Updating session data for sessionId: {}", sessionId);
        String sessionData = data + " (updated at " + System.currentTimeMillis() + ")";
        mockDatabase.put(sessionId, sessionData);
        return sessionData;
    }
    /**
     * Retrieve session data with caching
     */
    @Cacheable(value = CacheNames.CACHE_USER_SESSIONS, key = "#sessionId")
    public String getSessionData(String sessionId) {
        log.info("Cache MISS for session data, sessionId: {} - This would be a database call", sessionId);
        simulateSlowOperation();
        return mockDatabase.getOrDefault(sessionId, "No session data found").toString();
    }
    /**
     * Cache eviction example - remove specific entry
     */
    @CacheEvict(value = CacheNames.CACHE_PRODUCTS, key = "#id")
    public void invalidateProductCache(String id) {
        log.info("Invalidating cache for product ID: {}", id);
    }
    /**
     * Multiple cache operations example
     */
    @Caching(evict = {
            @CacheEvict(value = CacheNames.CACHE_USER_PREFERENCES, key = "#userId"),
            @CacheEvict(value = CacheNames.CACHE_USER_SESSIONS, key = "#sessionId")
    })
    public void logoutUser(String userId, String sessionId) {
        log.info("User logout - clearing user-related caches for userId: {}, sessionId: {}", userId, sessionId);
        // Perform actual logout operations
    }
    /**
     * Clear all entries from a cache
     */
    @CacheEvict(value = CacheNames.CACHE_TEMPORARY_TOKENS, allEntries = true)
    public void clearAllTokens() {
        log.info("Clearing all temporary token cache entries");
    }
    /**
     * Clear all entries from multiple caches
     */
    @Caching(evict = {
            @CacheEvict(value = CacheNames.CACHE_PRODUCTS, allEntries = true),
            @CacheEvict(value = CacheNames.CACHE_USER_PREFERENCES, allEntries = true),
            @CacheEvict(value = CacheNames.CACHE_USER_SESSIONS, allEntries = true),
            @CacheEvict(value = CacheNames.CACHE_TEMPORARY_TOKENS, allEntries = true)
    })
    public void clearAllCaches() {
        log.info("Clearing ALL cache entries from all caches");
    }
    /**
     * Conditional caching example
     */
    @Cacheable(
            value = CacheNames.CACHE_TEMPORARY_TOKENS,
            key = "#token",
            condition = "#token.length() > 10"
    )
    public String validateToken(String token) {
        log.info("Cache MISS for token validation, token: {} - This would be a database call", token);
        simulateSlowOperation();
        return "Token " + token + " is " + (token.length() > 15 ? "valid" : "invalid");
    }
    /**
     * Generate a random token for testing
     */
    public String generateToken() {
        String token = UUID.randomUUID().toString();
        log.info("Generated new token: {}", token);
        return token;
    }
    /**
     * Helper method to simulate slow database operations
     */
    private void simulateSlowOperation() {
        try {
            // Simulate database latency
            Thread.sleep(2000);
        } catch (InterruptedException e) {
            Thread.currentThread().interrupt();
        }
    }
}
```

https://www.spiceworks.com/tech/tech-101/articles/what-is-cache

https://docs.spring.io/spring-boot/reference/io/caching.html#io.caching.provider.simple

Previous issue

**Geliştirici olmak için izlediğim yol**

Next issue

**Useful Commands - Cheat Sheet**
