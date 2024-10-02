# Basic Authentication - In Memory DB

If you want to see spring security in action you can create a very simple example without any database. We will store some users in memory. Before we start let's add these dependencies to `pom.xml` file:

```markup
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-security</artifactId>
    </dependency>
    <dependency>
        <groupId>org.springframework.security</groupId>
        <artifactId>spring-security-test</artifactId>
        <scope>test</scope>
    </dependency>
```

Then we will create a `PasswordEncoderConfig` for hashing passwords. We should never keep passwords as plain text in database.

```java
@Configuration
public class PasswordEncoderConfig {

    @Bean
    public BCryptPasswordEncoder bCryptPasswordEncoder() {
        return new BCryptPasswordEncoder();
    }
}
```

After that we will create `SecurityConfig` class for configure spring security.

```java
@Configuration
@EnableWebSecurity
@RequiredArgsConstructor
@EnableMethodSecurity
public class SecurityConfig {

    private final PasswordEncoder passwordEncoder;

    private static final String[] IGNORED_PATHS = {
            "/swagger-resources/**",
            "/swagger-ui.html/**",
            "/swagger-ui/**",
            "/v3/api-docs/**",
            "/auth/**",
            "/public/**",
            "/h2-console/**"
    };

    @Bean
    public WebSecurityCustomizer webSecurityCustomizer() {
        return (web) -> Arrays.stream(IGNORED_PATHS)
                .forEach(path -> web.ignoring().requestMatchers(new AntPathRequestMatcher(path)));
    }

    @Bean
    public UserDetailsService users() {
        UserDetails user =
                User.builder()
                        .username("user")
                        .password("pass")
                        .passwordEncoder(passwordEncoder::encode)
                        // .password(passwordEncoder.encode("pass"))
                        .roles("USER")
                        .build();
        UserDetails admin =
                User.builder()
                        .username("admin")
                        .password(passwordEncoder.encode("pass"))
                        .roles("USER", "ADMIN")
                        .authorities("create", "read")
                        .build();
        UserDetails mod =
                User.builder()
                        .username("mod")
                        .password(passwordEncoder.encode("pass"))
                        .roles("MOD")
                        .build();
        return new InMemoryUserDetailsManager(user, admin, mod);
    }

    @Bean
    public SecurityFilterChain filterChain(HttpSecurity httpSecurity) throws Exception {
        httpSecurity
                .headers(x -> x.frameOptions(HeadersConfigurer.FrameOptionsConfig::disable))
                .csrf(AbstractHttpConfigurer::disable)
                .cors(Customizer.withDefaults())
//                .formLogin(AbstractHttpConfigurer::disable)
                .authorizeHttpRequests(x -> x.anyRequest().authenticated())
                .httpBasic(Customizer.withDefaults());
        return httpSecurity.build();
    }


    @Bean
    public WebMvcConfigurer corsConfigurer() {
        return new WebMvcConfigurer() {
            @Override
            public void addCorsMappings(@NonNull CorsRegistry registry) {
                registry.addMapping("/**").allowedMethods("*");
            }
        };
    }

}
```

* IGNORED\_PATHS: if you want to allow request to certain endpoints you should put it into array. Most of the time we allow `open api` (aka Swagger) endpoints and login/register endpoints.
* To create users we should add a `UserDetailsService` bean. Normally we should call database to retrieve user. However in this example we will use in-memory db.
* filterChain: This is for setting our details like cors, csrf, authorize http requests and more. Also we add `headers frame options` to allow h2 database console endpoints. Not necessary if you are not using h2 database.
* corsConfigurer: CORS (Cross-Origin Resource Sharing) is a security feature that controls which domains can make requests to your server. In Spring Boot, you can configure CORS using a `corsConfigurer`. Allowing all origins with a wildcard (`*`) is not recommended in production because it opens up your server to requests from any domain, which can be a security risk. Instead, specify only trusted domains to ensure better security.
* formLogin: By default spring security has its own mvc form login. If you are not making mvc project just disable it.

### How to implement security to our controllers?

Actually you implemented security already however you can make some customizations for specific controllers. Here is an example:

```java
@RestController
@RequestMapping("/private")
public class PrivateTestController {

    @GetMapping
    public ResponseEntity<String> sayHelloToAnyAuthenticated() {
        return ResponseEntity.ok("Hello Any Authenticated! This is private endpoint");
    }

    // @PreAuthorize("hasRole('ROLE_ADMIN')") // need ROLE_ prefix
    @PreAuthorize("hasAuthority('create')")
    @GetMapping("/admin")
    public ResponseEntity<String> sayHelloToAdmin() {
        return ResponseEntity.ok("Hello Admin! This is private endpoint");
    }

    @PreAuthorize("hasAnyRole('ROLE_ADMIN','ROLE_USER')")
    @GetMapping("/user")
    public ResponseEntity<String> sayHelloToUser() {
        return ResponseEntity.ok("Hello User! This is private endpoint");
    }
}


@RestController
@RequestMapping("/public")
public class PublicTestController {

    @GetMapping
    public ResponseEntity<String> sayHello() {
        return ResponseEntity.ok("Hello! This is public endpoint");
    }
}

```

### How will we test endpoints?

To send request using basic authentication we should send our username and password base64 format like this:

<pre class="language-bash"><code class="lang-bash"># username: admin
<strong># password: pass
</strong>[username]:[pass] => admin:pass => YWRtaW46cGFzcw==
</code></pre>

Hopefully postman converts it to base 64 automatically

<figure><img src="../../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

```
curl --location 'localhost:8080/private' \
--header 'Authorization: Basic YWRtaW46cGFzcw=='
```

Github: [https://github.com/gurkanucar/java-spring-learning/tree/master/spring-security/1-in-memory-auth](https://github.com/gurkanucar/java-spring-learning/tree/master/spring-security/1-in-memory-auth)
