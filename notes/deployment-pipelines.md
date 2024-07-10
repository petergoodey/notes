# Deployment Pipelines

## Continuous Delivery

**Code should always be in a releasable state!**

### Automated Pipeline considerations

* Unit tests
* Integration tests
* Mutation Testing
* Code coverage analysis
* SCA
* Static Application Security Testing
* Acceptance Tests
* IaC
* Deployment
* Deployment testing

## Deployment Strategies

Ideally code should be deployed directly to production after a unit of work. But we can use the following strategies:

* Canary
* Blue green
* Fine grained traffic routing (with a service mess like istio using headers)
* Automated rollouts and promotions

### Tooling

* [Argo Rollouts](https://argoproj.github.io/rollouts/)
