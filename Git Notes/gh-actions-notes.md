# GITHUB ACTIONS EXPLAINED

## What is Github Actions?

- Powerful automation tool that allows you to define "workflows" for software projects

**"WORKFLOWS":**

- made up of one or more **jobs**
- jobs are made up of one or more **steps**
- steps perform a **specific action** (i.e. running a script or deploying the application)

**"ACTIONS":**

- used for a wide range of tasks:
  - building and testing code
  - deploying application
  - sending notifications
  - publishing to a package registry
- defined using `YAML` syntax or triggered by events (i.e. new commit or pull request being opened)

**HOW TO USE GITHUB ACTIONS?**

- Create a YAML file in the repository's `.github/workflows` directory
  - YAML file extension: `file.yml`

- The YAML file defines:
  - the workflow
  - events that trigger actions
  - jobs that make up the workflow
  - steps that each job performs
  - environment variables
  - secrets
  - other config options

- Github automatically runs the file after it is created whenever specified events occur
- "Actions" tab in repo allows for monitoring the progress of workflows
  - status of each job and step
  - view logs
  - re-run failed workflows

**COMMON USAGE:**

**Continuous integration and continuous deployment (CI/CD) of your code:**

- used to automate the process of building, testing and deploying code
- when new commit is pushed to repo, GH can automatically run the test suite and if everything passes, deploy the application to a staging or production evironment
  - helps to ensure code is always in a deployable state and reduces risk of introducing bugs or errors in production

**Running tests and linters to ensure code quality:**

- use to run various types of tests (i.e. unit tests, integration tests, end-to-end tests, etc.)
- run linters and other static analysis tools to ensure code meets certain standards and is free from common errors and vulnerabilities

**Building and packaging application for distribution:**

- used to automate the process of building and packages you application for distribution
  - compiling code, creating executable files, generating documentation, etc.

**Automating release management and versioning:**

- helps to automate the process of releasing new versions of software
  - automatically updating version numbers, generating release notes, and publishing releases to GH or other package registries
- helps to streamline release process and reduce risk of errors/mistakes

**Sending notifications to team or customers:**

- used to send notifications to team/customers
  - sending emails or messages to inform them when new features are released, when bugs are fixed, or when important events occur in development process
- helps to keep everyone on the same page and ensures that everyone is aware of what is happening with project
