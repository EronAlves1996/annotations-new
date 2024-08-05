#### Exercise 1: Simple Dependency

**Scenario:**

- A method calculates the total price of a shopping cart.
- The method takes a `Product` object as a parameter.
- `Product` has complex logic to calculate its price based on various factors.

**Task:**

- Create an interface `ProductInterface` with a `getPrice()` method.
- Create two implementations: `RealProduct` and `TestProduct`.
- Modify the method to accept `ProductInterface` instead of `Product`.
- Write tests using `TestProduct` to isolate the pricing logic.

#### Exercise 2: Database Dependency

**Scenario:**

- A method retrieves customer data from a database.
- The method takes a `DatabaseConnection` object as a parameter.

**Task:**

- Create an interface `DatabaseConnectionInterface` with methods for querying data.
- Create implementations: `RealDatabaseConnection` and `TestDatabaseConnection`.
- Modify the method to accept `DatabaseConnectionInterface`.
- Write tests using `TestDatabaseConnection` to simulate database interactions.

#### Exercise 3: External Service Dependency

**Scenario:**

- A method fetches weather data from an external API.
- The method takes a `WeatherService` object as a parameter.

**Task:**

- Create an interface `WeatherServiceInterface` with methods for fetching weather data.
- Create implementations: `RealWeatherService` and `TestWeatherService`.
- Modify the method to accept `WeatherServiceInterface`.
- Write tests using `TestWeatherService` to mock API responses.

#### Exercise 4: Complex Parameter Object

**Scenario:**

- A method calculates shipping costs based on a `ShippingDetails` object.
- `ShippingDetails` has multiple properties and complex validation logic.

**Task:**

- Create an interface `ShippingDetailsInterface` with appropriate methods.
- Create implementations: `RealShippingDetails` and `TestShippingDetails`.
- Modify the method to accept `ShippingDetailsInterface`.
- Write tests using `TestShippingDetails` to control shipping details for different scenarios.

### Additional Considerations

- **Interface Design:** Keep interfaces focused and minimal. Avoid over-engineering.
- **Test Doubles:** Explore using test doubles (mocks, stubs, fakes) to isolate dependencies effectively.
- **Dependency Injection:** Consider using a dependency injection framework for managing dependencies.
- **Refactoring:** After adapting the parameter, evaluate if further refactoring is necessary to improve code clarity and maintainability.