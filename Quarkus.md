* JSON is the default content-type
* Disable with `quarkus.restaeasy-json.default=-json`
* Use `@ResponseStatus`to change response status
* Mapping exceptions is simple
	* Provide an implementation of `ExceptionMapper`
	* Annotate with `@Provider` (the annotation for providing implementation for an `interface`)
* `mp.jwt.verify.publickey.location`: can point to a remote URL if we are using an external authorization service
* `@ConfigProperty` acts like `@Value` from Spring
* Quarkus security will parse and verify the token, and can inject the `JsonWebToken` as a request scoped bean for each request
* Quarkus @RolesAllowed permits an endpoint for some roles
* `quarkus-test-security-jwt` to test applications with a JWT security layer