# Automation practices and tools

Automation helps developer, operation and infrastructure teams to reduce and standardize repetitive tasks, easing scalability and management of the applications and systems involved in projects.

## Continuous Integration

Continuous Integration (CI) is a development practice where developers integrate code into a shared repository frequently, preferably several times a day. Each integration can then be verified by an automated build and automated tests. While automated testing is not strictly part of CI it is typically implied.

Here are described some practices and tools that will help with CI:

### DevOps Toolchains

A DevOps toolchain is a set of tools that automates the tasks of developing and deploying an app. It helps to integrate pipelines with different tools that runs triggered by Git repository updates.

[Info on DevOps Toolchains](https://www.ibm.com/cloud/architecture/toolchains/)

### Contract Testing with PACT

Contract testing is a methodology for ensuring that two separate systems (such as two microservices) are compatible with one another. It captures the interactions that are exchanged between each service, storing them in a contract, which can then be used to verify that both parties adhere to it.

Pact automates contract testing and enables it to be added to a continuous integration pipeline.

In consumer-driven contract testing it is the consumer who defines the contract in terms of the expected interactions, the data structure, and the expected responses. That contract can then be used on the consumer-side to mock the interactions and validate the consumer behavior. More importantly, the contract can be shared with the provider of the interaction so that the provider’s responses can be validated to ensure the consumer’s expectations are met.

In the Pact framework, the contract is called a pact. A pact consists of one or more interactions that ensure the correct behavior of the microservice.

[Info on PACT](https://cloudnativetoolkit.dev/tools/contract-testing-with-pact)

### End to End testing with Cypress and BDD

Behavior-driven development is an Agile software development process that promotes collaboration between developers, software testers (QA), and the non-technical, business side in a software development process. The outcomes of their collaboration are structured behavior stories which are requirements for product owners, acceptance criteria for developers, description for stakeholders, test cases, and automation scripts for testers.

Cypress is a front end testing tool built for the web applications. It addresses pain points developers and QA engineers face when testing modern applications.

[Info on Cypress](https://docs.cypress.io/guides/overview/why-cypress.html#In-a-nutshell)

## Continuous Delivery

Continuous delivery (CD) is a software engineering approach in which teams produce software in short cycles, ensuring that the software can be reliably released at any time. It aims at building, testing, and releasing software with greater speed and frequency. 

Here are described some practices and tools that will help with CD:

### Container Registry

A Container Registry is a Docker registry for storing OCI images. When deploying an application to a Kubernetes or OpenShift cluster, the cluster creates containers using the images in the registry. To package an application for deployment, the runtime must be built into an image that is stored in the registry.

[Info on Container Registry](https://cloudnativetoolkit.dev/tools/ibm-cloud-container-registry)

### CD with ArgoCD

Argo CD is a declarative, GitOps continuous delivery tool for Kubernetes and OpenShift. The deployment environment is a namespace in a container platform like Kubernetes or Red Hat OpenShift. Argo CD models a collection of applications as a project and uses a Git repository to store the application’s desired state. Argo CD is flexible in the structure of the application configuration represented in the Git repository.

Argo CD compares the actual state of the application in the cluster with the desired state defined in Git and determines if they are out of sync. When it detects the environment is out of sync, Argo CD can be configured to either send out a notification to kick off a separate reconciliation process or Argo CD can automatically synchronize the environments to ensure they match.

[Info on ArgoCD](https://cloudnativetoolkit.dev/tools/argocd)

## Infrastructure Automation

Infrastructure as Code is the process of managing and provisioning computer data centers through machine-readable definition files, rather than physical hardware configuration or interactive configuration tools. It defines the logic used to provision infrastructure as versioned artifacts in the same way that code artifacts have traditionally been handled. There are a number of different tools and frameworks available that enable this type of approach.

### Infrastructure Automation with Terraform

Terraform is a tool for building, changing, and versioning infrastructure safely and efficiently. Terraform can manage existing and popular service providers as well as custom in-house solutions.

Configuration files describe to Terraform the components needed to run a single application or your entire datacenter. Terraform generates an execution plan describing what it will do to reach the desired state, and then executes it to build the described infrastructure. As the configuration changes, Terraform is able to determine what changed and create incremental execution plans which can be applied.

[Info on Terraform](https://www.terraform.io/intro/index.html)

### Infrastructure Automation as a Service with Schematics

With IBM Cloud Schematics, you can organize your IBM Cloud resources across environments by using workspaces. Every workspace points to a set of Terraform configuration files, which build a Terraform template. 

[Info on Schematics](https://cloud.ibm.com/docs/schematics?topic=schematics-about-schematics)

## Development

Here are described some practices and tools that will help smooth the development experience.

### Dev containers

[Info on devcontainers (and pros & cons)](https://medium.com/@stoz_das/getting-started-with-dev-containers-ad22a293037f){: .hide-on-pdf }

[Dev containers](https://code.visualstudio.com/docs/remote/containers) are a feature of [VS Code](https://code.visualstudio.com/) (Visual Studio Code, an open-source IDE developed by Microsoft). They allow to describe a development environment as code in the form of a Docker container. The image of the container will be based on the main language (e.g. Java) and will install on top of it all the required development tools (e.g. Maven).

This way, any developer using the `dev container` will have the same set of tools and configuration, that is proven to work, and won't have to spend any time configuring their IDE or station. Since it runs on a Docker container, multiple developers on different host OSs will work on the same underlaying technology. Since the final application will also run in a container, having a development environment that is the most close to the production environment, will help reduce bugs, improve reproducibility, and so on and so forth.
