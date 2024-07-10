# Application Code Organisation

## Repositories: To Monorepo or not to Monorepo

Software that versions together, deploys together and changes together, should be collocated.

Monorepos generally projects that share lots of dependencies. However this would tend to imply a tight coupling.

In the early days of a project it might generally better to start a new project with a single repo to reduce code deduplication through re-using types used in microservices - e.g. logging, authentication and pact-testing.

These feature folders can also be vertically sliced.

### Put Common Code in versioned NuGet packages

In microservice architectures especially I have seen so much copied-and-pasted code between microservices. This is incidentally an argument for mono repos.

Common areas where code can be re-used are:

* Logging
* Error Handling
* Authentication
* Authorisation
* HTTP headers
* Retry Policies (e.g. Polly)
* Circuit Breakers
* Pact Testing (Provider and Consumer)
* Integration Test Harnesses (e.g. customised WebApplicationFactory)

### Keep Packages Up-to-date

### Use .NET Alpine Docker Images in production

### Publish as self-contained for Productions