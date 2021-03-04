The following decisions have been made in the course of developing this architecture. They are captured here to provide the necessary background to those interested in deeper rationale for the architecture.
Each decision is made in accordance to the [Architecture Principles mentioned here](../03-arch-principles/arch-principles.md)

### 4.4.1 Architectural Decision AD-001

| **Architectural Decision**     | Java Framework for backend microservices |
| -------------------------------| -------------------- |
| **Issue or Problem Statement** | Accelerate the microservices development  |
| **Motivation**                 | Alerce's developers already have java skills |
| **Alternatives**               | Golang, Python, C++, Ruby |
| **Decision**                   | Implement backend microservices with a java framework |
| **Justification**              | Easy to integrate and is the most popular language for microservices  |
| **Implications**               | Expedite the move to new framework and platform |
| **Derived Requirements**       | N/A  |
| **Related Decisions**          | N/A  |

### 4.4.2 Architectural Decision AD-002

| **Architectural Decision**     | Single-page application for frontend |
| -------------------------------| -------------------- |
| **Issue or Problem Statement** | Accelerate the microservices development  |
| **Motivation**                 | Alerce don't want to use JSP but they will be willing to use something like VUE, Angular or React. |
| **Alternatives**               | Traditional frontend application using for example JSF |
| **Decision**                   | Implement frontend microservices with an SPA framework |
| **Justification**              | It is the most popular framework for frontend. Better learning curve. |
| **Implications**               |  |
| **Derived Requirements**       | N/A  |
| **Related Decisions**          | N/A  |

### 4.4.3 Architectural Decision AD-003

| **Architectural Decision**     | API gateway |
| -------------------------------| -------------------- |
| **Issue or Problem Statement** | Abstract the communication between client applications and internal microservices |
| **Motivation**                 | An API Gateway allows for the composition of microservices into client-ready services and removes coupling between microservices and client apps. Enabling API management, consumption monitoring and monetization |
| **Alternatives**               | Direct communication with microservices |
| **Decision**                   | Expose API through an API gateway, implementing an API management solution |
| **Justification**              | Broad set of offerings to accompany its API management with features including integration, API testing, API monitoring, etc.|
| **Implications**               |  |
| **Derived Requirements**       |  |
| **Related Decisions**          |  |

### 4.4.4 Architectural Decision AD-004

| **Architectural Decision**     | Event-Driven Architecture |
| -------------------------------| -------------------- |
| **Issue or Problem Statement** | Responds to events in real-time, as they happen, delivers responsive customer experiences, brings real-time intelligence to the application and decouple services |
| **Motivation**                 | Loose coupling between components/services; Ability to scale individual components; Processing components can be developed independent of each other; High cloud affinity; Asynchronous nature. As well as ability to throttle workload; Fault Tolerance and better resiliency; Ability to build processing pipelines; Availability of sophisticated event brokers reduce code complexity; A rich palate of proven [Enterprise Integration Patterns](https://www.enterpriseintegrationpatterns.com/) |
| **Alternatives**               | Classic layered architecture pattern (n-tier architecture pattern)  |
| **Decision**                   | Implement an Event-Driven Architecture |
| **Justification**              |  |
| **Implications**               |  |
| **Derived Requirements**       | Database per service |
| **Related Decisions**          |  |

### 4.4.5 Architectural Decision AD-005

| **Architectural Decision**     | Messaging service |
| -------------------------------| -------------------- |
| **Issue or Problem Statement** | A way to intercept and inject events to and from system components is needed |
| **Motivation**                 | To implement the EDA is required an asynchronous message delivery system  |
| **Alternatives**               | Having chosen an event-driven architecture, there is no alternative to a messaging system. |
| **Decision**                   | Use a messaging service to manage events |
| **Justification**              |  |
| **Implications**               |  |
| **Derived Requirements**       |  |
| **Related Decisions**          | [AD-004](#444-architectural-decision-ad-004) |

### 4.4.6 Architectural Decision AD-006

| **Architectural Decision**     | SAGA Pattern |
| -------------------------------| -------------------- |
| **Issue or Problem Statement** | With the adoption of one data source per microservice, there is an interesting challenge on how to support long running transaction cross microservices. With event backbone two phase commit is not an option |
| **Motivation**                 | Some business transactions span multiple service so you need a mechanism to implement transactions that span services. With database per service, data are in different databases/schemas so it's not possible to use a local ACID transaction |
| **Alternatives**               | N/A|
| **Decision**                   | Adopt SAGA pattern to manage distributed transaction using one of the two coordinators: Choreography or Orchestration |
| **Justification**              |  |
| **Implications**               | A compensation process must be implemented |
| **Derived Requirements**       |  |
| **Related Decisions**          | [AD-004](#444-architectural-decision-ad-004) |

### 4.4.7 Architectural Decision AD-007

| **Architectural Decision**     | Command Query Responsibility Segregation (CQRS) |
| -------------------------------| -------------------- |
| **Issue or Problem Statement** | In a microservice architecture, data are managed by several microservices. How to merge information from different microservices? |
| **Motivation**                 |  |
| **Alternatives**               | API Composition: implement a query by defining an API Composer, which invoking the services that own the data and performs an in-memory join of the results. |
| **Decision**                   | Implement CQRS pattern separating the writing model from the reading model. The read model is a database view, which is a read-only replica that is designed to support required queries. The application keeps the replica up to data by subscribing to events published by the service that own the data.|
| **Justification**              |  |
| **Implications**               |  |
| **Derived Requirements**       |  |
| **Related Decisions**          | [AD-004](#444-architectural-decision-ad-004) |

### 4.4.8 Architectural Decision AD-008

| **Architectural Decision**     | Cloud managed services |
| -------------------------------| -------------------- |
| **Issue or Problem Statement** | How to use services such as databases, message services and so on? In a cloud environment, you can choose between services that are managed by the cloud provider or managed by yourself.    |
| **Motivation**                 | Cloud services are managed by cloud provider so you don't need to configure and manage them yourself (for example HA/DR or maintenance tasks|
| **Alternatives**               | Create services inside the cluster managed by Alerce |
| **Decision**                   | Use cloud managed services as much as possible |
| **Justification**              |  |
| **Implications**               |  |
| **Derived Requirements**       |  |
| **Related Decisions**          |  |

### 4.4.9 Architectural Decision AD-009

| **Architectural Decision**     | Kubernetes/RedHat OpenShift namespaces to manage customer tenancy |
| -------------------------------| -------------------- |
| **Issue or Problem Statement** | How to segregate Alerce's customer application?  |
| **Motivation**                 | Maintenance and management is easier.  Meets required segregation and customization requirements|
| **Alternatives**               | Kubernetes/RedHat OpenShift per customer |
| **Decision**                   | Use namespaces per customer |
| **Justification**              | Cost. Multiple clusters is more expensive than single cluster with multiple namespaces |
| **Implications**               | Each customer will have its configuration stored in an appropriate location (e.g., config maps, key-value database, etc.). |
| **Derived Requirements**       |  |
| **Related Decisions**          |  |

