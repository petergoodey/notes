# Application Security

## Keep Packages Up-to-date

* [Dependabot](https://github.com/dependabot)
* [Renovate](https://www.mend.io/renovate/)

## Use Alpine Docker Images in production

When we switched to alpine images most of the CVEs we were getting from Trivy melted away.

## Publish as self-contained for Productions

## Use SCA and SAST Scanners

* Checkmarx
* Sonarqube

## Use Library Scanners

* [Snyk](https://snyk.io/)
* [NuGetDefense.Tool](https://www.nuget.org/packages/NuGetDefense.Tool)

## Scan generated container

* [Trivy](https://trivy.dev/)

## Authentication

## RBAC

## API Security

* JWT

## Secrets Leaking

* [Article](https://docs.github.com/en/code-security/secret-scanning/configuring-secret-scanning-for-your-repositories)

## Remove shell from Production images

Don't allow root access or shell.
