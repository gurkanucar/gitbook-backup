# Development Standards

#### **Service Architecture and Design**

1. **Business Logic Separation**\
   Business logic should not be written in the controller layer. Keep the controller layer focused on request/response handling and leave business logic to the service layer.
2. **Optimize API Calls**\
   Instead of making multiple sequential API calls, prefer batch requests when possible to reduce network latency and improve performance.
3. **Use Circuit Breaker for API Integrations**\
   Implement a circuit breaker pattern in API integration calls to avoid cascading failures. This ensures that the system remains responsive during external service downtime.
4. **Rate Limiting**\
   Apply rate limiting to all services to prevent overloading the system and ensure fair usage across clients.
5. **Set Timeout for Services**\
   All services should have a defined timeout to prevent hanging operations and improve overall system responsiveness.
6. **Timeout for Feign Clients**\
   Add timeouts for Feign clients to prevent long waits during service calls and potential memory leaks.
7. **Retry Mechanism**\
   Add retry mechanism while calling remote services.



***

#### **Data Handling and Persistence**

1. **Prefer Optimistic Locking**\
   In scenarios with potential data conflicts, always use optimistic locking. Avoid using pessimistic locking, which can lead to deadlocks and poor performance.
2. **Aggregate Operations at Database Level**\
   Perform aggregate functions such as `COUNT`, `SUM`, `AVG` directly at the database level to minimize memory consumption and improve performance.
3. **Use Indexes for Entities**\
   Consider creating indexes on entities for optimized query performance, especially for frequently queried fields.
4. **Implement Caching**\
   Integrate caching for frequently accessed data, especially for lookup tables or static data, to reduce database load and improve response times.
5. **Check for Division by Zero**\
   Ensure that division by zero is always checked to prevent runtime errors and system crashes.

***

#### **Handling Large Data Sets and Bulk Operations**

1. **Avoid Service Calls in Loops**\
   Do not make service calls within loops, as it leads to performance degradation. Instead, use bulk service operations.
2. **Apply Pagination for Large Data Sets**\
   If more than 50 records are being returned, apply pagination to reduce memory usage and response times.
3. **Asynchronous Processing for Long-running Tasks**\
   For long-running tasks such as exporting reports, use asynchronous processing where possible. Notify users via WebSocket or other methods when the task is complete.

***

#### **Queue and Retry Mechanisms**

1. **Implement Retry Mechanism in Queues**\
   When using queues, implement a retry mechanism with exponential backoff to prevent infinite consumption loops. Messages that cannot be processed should be logged as errors in the database or removed from the queue.

***

#### **Code Standards and Quality**

1. **Class and Method Size**\
   Keep classes under 500 lines and methods under 50 lines to ensure code maintainability, readability, and testability.
2. **Null and Empty Checks**\
   Always perform null and empty checks before operating on data to avoid runtime exceptions and bugs.
3. **Date Format Handling**\
   Use a converter class for handling date formats consistently across the application to prevent date-related bugs.
4. **Recursive Usage**\
   Avoid recursion where possible, as it can lead to stack overflow issues and performance problems.
5. **Prefer Guard Clauses**\
   In `if-else` conditions, prefer guard clauses to reduce nesting and increase the clarity of code.

***

#### **Logging and Error Handling**

1. **Proper Logging**\
   Implement logging infrastructure using appropriate log levels (`INFO`, `WARN`, `ERROR`) to track system behavior and issues effectively.
2. **Meaningful Error Responses**\
   Return meaningful error messages in API responses. Ensure that all `4xx` errors are handled properly and avoid returning generic `500` errors to the front end.

***

#### **API Documentation and Standards**

1. **API Documentation**\
   Ensure that detailed documentation is created for all APIs using tools like Swagger or OpenAPI to improve developer experience and ease of integration.

***

#### **Resource Management**

1. **Configure Resource Pools**\
   Properly configure resource values for connection pools, thread pools, and database connection pools to optimize resource usage and prevent resource exhaustion.

***

#### **Conventional Commits**

Adopt the Conventional Commits standard for version control:

* `feat`: Introduce a new feature.
* `fix`: Fix a bug.
* `docs`: Documentation changes.
* `style`: Code style changes (formatting, missing semi-colons, etc.).
* `refactor`: Code refactoring without changing functionality.
* `perf`: Performance improvements.
* `test`: Add or modify tests.
* `chore`: Maintenance tasks (e.g., build processes, tooling).

***

#### **Summary of Consequences**

1. **Performance**: API batch requests, bulk operations, caching, and pagination improve overall system performance.
2. **Reliability**: Circuit breakers, rate limiting, retry mechanisms, and optimistic locking ensure system reliability under load.
3. **Maintainability**: Code size limits, guard clauses, and proper logging help maintain code quality.
4. **Scalability**: Queue mechanisms, asynchronous tasks, and connection pools help scale the system efficiently.
5. **Consistency**: Null checks, division by zero checks, and date format handling ensure data consistency and avoid runtime issues.

This reordering groups related practices together, highlighting the importance of each entry based on its consequences and effects on performance, reliability, scalability, and maintainability.
