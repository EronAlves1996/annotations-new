* Normally, for JWT authentication, you'll want an external identity manager to authenticate and generate JWT's
* Your application only need to verify the bearer token upon any http received request
* Identity and Access Management tool
* The IAM tool holds the private key and the application holds the public key JWT. The application issues that for the IAM tool to verify it
* JWT tokens are ideal for expire in short time and provide a refresh token. An IAM tool already have this functionality
* The roles in JWT are a set describing the roles in the `groups`section of payload
* I find JWT can be a lot insecure, but it can be hashed by a bidirectional hash function, keeping a private key for verifying that JWT is legit