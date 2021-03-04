This section describes the recommended technologies for each of the components or features that are defined in the solution.

### 4.5.1 Compute Platform

The solution needs a platform to run the workloads of the system.

**Recommended technology**

| **Name**                       | Red Hat OpenShift |
| -------------------------------| -------------------- |
| **Definition**                 | Red Hat OpenShift is an enterprise-grade container platform based on industry standards, Docker and Kubernetes |
| **Pros**                       | You can deploy Red Hat OpenShift as a managed service on your preferred cloud provider for a seamless experience on Azure, AWS, IBM Cloud, or Google Cloud or On-Prem deployments. Easy to manage tools based on the Operator scheme. |
| **Cons**                       | Infrastructure would need more resources than other alternatives. On premises has to be managed. |
| **URL**                        | https://www.openshift.com/ |

??? "Other alternatives"

    | **Name**                       | IBM Cloud Kubernetes Service (IKS)|
    | -------------------------------| -------------------- |
    | **Definition**                 | Managed Kubernetes platform on IBM Cloud |
    | **Pros**                       | Managed service. Low workload overhead. |
    | **Cons**                       | Not as many features as OpenShift. It only runs on IBM Cloud. |
    | **URL**                        | https://www.ibm.com/cloud/container-service/ |

    | **Name**                       | Amazon Elastic Kubernetes Service (EKS) |
    | -------------------------------| -------------------- |
    | **Definition**                 | Managed Kubernetes platform on AWS Cloud |
    | **Pros**                       | Managed service. Low workload overhead. |
    | **Cons**                       | Not as many features as OpenShift. It only runs on AWS Cloud. |
    | **URL**                        | https://aws.amazon.com/eks/ |

    | **Name**                       | Azure Kubernetes Service (AKS) |
    | -------------------------------| -------------------- |
    | **Definition**                 | Managed Kubernetes platform on Azure Cloud |
    | **Pros**                       | Managed service. Low workload overhead. |
    | **Cons**                       | Not as many features as OpenShift. It only runs on Azure Cloud. |
    | **URL**                        | https://azure.microsoft.com/services/kubernetes-service/ |

    | **Name**                       | Google Kubernetes Engine (GKE) |
    | -------------------------------| -------------------- |
    | **Definition**                 | Managed Kubernetes platform on Google Cloud |
    | **Pros**                       | Managed service. Low workload overhead. |
    | **Cons**                       | Not as many features as OpenShift. It only runs on Google Cloud. |
    | **URL**                        |[ https://azure.microsoft.com/services/kubernetes-service/](https://cloud.google.com/kubernetes-engine) |



### 4.5.2 Authentication / Authorization

The solution needs a centralized Authentication an Authorization mechanism. This feature allows each user login and role definition for all the applications in the solution. 

**Recommended technology**

| **Name**                       | IBM AppID |
| -------------------------------| -------------------- |
| **Definition**                 | IBM Cloud App ID allows to easily add authentication to web and mobile apps with zero code changes and no redeploy required |
| **Pros**                       | Works as an external service. Provides support for OpenID Connect, OAuth 2.0, and SAML. |
| **Cons**                       | Service needs to be managed on IBM Cloud.  |
| **URL**                        | https://www.ibm.com/cloud/app-id |

??? "Other alternatives"

    | **Name**                       | Keycloak |
    | -------------------------------| -------------------- |
    | **Definition**                 | Keycloak is an open source Identity and Access Management solution aimed at modern applications and services |
    | **Pros**                       | Works as an OpenShift Operator. Provides support for OpenID Connect, OAuth 2.0, and SAML. Keycloak has built-in support to connect to existing LDAP or Active Directory servers. |
    | **Cons**                       | Service needs to be managed in a Red Hat OpenShift Platform.  |
    | **URL**                        | https://www.keycloak.org/ |

    | **Name**                       | Amazon Cognito |
    | -------------------------------| -------------------- |
    | **Definition**                 | Amazon Cognito lets you add user sign-up, sign-in, and access control to your web and mobile apps quickly and easily |
    | **Pros**                       | Works as an external service. Provides support for OpenID Connect, OAuth 2.0, and SAML. |
    | **Cons**                       | Service needs to be managed on AWS Cloud.  |
    | **URL**                        | https://aws.amazon.com/cognito/ |

    | **Name**                       | Istio Role-Based Access Control (RBAC) |
    | -------------------------------| -------------------- |
    | **Definition**                 | Istio Role-Based Access Control (RBAC) provides namespace-level, service-level, method-level access control for services in the Istio Mesh |
    | **Pros**                       | Low configuration needed. Built-in in istio. |
    | **Cons**                       | It needs an external Identity Provider. It needs an Istio mesh. |
    | **URL**                        | https://istio.io/v1.1/docs/reference/config/authorization/istio.rbac.v1alpha1/ |

### 4.5.3 Logging / Monitoring

Logging and monitoring is an essential aspect of an incident response strategy.

**Recommended technology**

| **Name**                       | EFK stack            |
| -------------------------------| -------------------- |
| **Definition**                 | "EFK" is the acronym for: Elasticsearch (search and analytics engine), Fluentd (gathers logs from nodes and feeds them to Elasticsearch), and Kibana (data-visualization) |
| **Pros**                       | Open Source Software. Already integrated into OpenShift Container Platform. |
| **Cons**                       |   |
| **URL**                        | https://docs.openshift.com/container-platform/4.4/logging/cluster-logging.html#cluster-logging-about-components_cluster-logging |

| **Name**                       | Prometheus/Grafana            |
| -------------------------------| -------------------- |
| **Definition**                 | [Prometheus](https://prometheus.io/) provides monitoring of cluster components and includes a set of alerts to immediately notify the cluster administrator. Monitoring dashboards are managed by [Grafana](https://grafana.com/). |
| **Pros**                       | Open Source Software. Already integrated into OpenShift Container Platform. |
| **Cons**                       |   |
| **URL**                        | https://docs.openshift.com/container-platform/4.4/monitoring/cluster_monitoring/about-cluster-monitoring.html |

??? "Other alternatives"

    | **Name**                       | SysDig               |
    | -------------------------------| -------------------- |
    | **Definition**                 | Sysdig is a simple tool for deep system visibility, with native support for containers. |
    | **Pros**                       | Native support for all Linux tech, including Docker, Kubernetes, Mesos, etc. Collect all types of data including Docker and Kubernetes event logs, as well as metadata from container orchestration tools. Filters for most common services. |
    | **Cons**                       | Need to install kernel headers on the host OS. It takes a bit of time to get used to the UI. |
    | **URL**                        | https://sysdig.com/  |

    | **Name**                       | LogDNA               |
    | -------------------------------| -------------------- |
    | **Definition**                 | LogDNA allows to easily aggregate and search application and server logs within a single platform. |
    | **Pros**                       | Aggregation of all event streams. Great Kubernetes integration. |
    | **Cons**                       | Some lag in log processing. |
    | **URL**                        | https://logdna.com/  |

### 4.5.4 Caching

The most frequent queries of static data can be cached in each module in order to improve the overall system's performance.

**Recommended technology**

| **Name**                       | Redis                |
| -------------------------------| -------------------- |
| **Definition**                 | Redis is an in-memory data structure store, used as a database, cache and message broker. |
| **Pros**                       | Fast. Easy and simple to use. Flexible data structures. Zero downtime or performance impact while scaling up or down. Open Source and stable. |
| **Cons**                       | Lack of some basic permissions. The whole dataset is on RAM, this can be expensive. |
| **URL**                        | https://redis.io/ |

??? "Other alternatives"

    | **Name**                       | memcached            |
    | -------------------------------| -------------------- |
    | **Definition**                 | High-performance, distributed memory object caching system. |
    | **Pros**                       | No data types. Small overhead memory. |
    | **Cons**                       | Small key (250B max) and values (1MB max). |
    | **URL**                        | https://memcached.org/ |

### 4.5.5 Observability

Observability is everything you need to find out why something is not working. It consists of three pillars:
- Logging
- Monitoring
- Metrics

Complex solutions needs to provide observability and configuration into the service mesh.

**Recommended technology**

| **Name**                       | Kiali                |
| -------------------------------| -------------------- |
| **Definition**                 | Kiali is a management console for Istio-based service mesh. It helps in understanding the structure of the service mesh by inferring the topology, and also provides the health of your mesh.|
| **Pros**                       | Visualize and provide insights into the features, integration with Jaeger and Grafana for tracing and advanced queries respectively |
| **Cons**                       | Consume some resources from cluster to operate |
| **URL**                        | https://kiali.io/ |

| **Name**                       | Jaeger               |
| -------------------------------| -------------------- |
| **Definition**                 | Jaeger is a software system that serves to detect operations between distributed services. It is used to monitor complex microservice environments and to solve the problems associated with them. |
| **Pros**                       | Open source |
| **Cons**                       | Consume some resources from cluster to operate |
| **URL**                        | https://www.jaegertracing.io/ |

??? "Other alternatives"

    | **Name**                       | Istio                |
    | -------------------------------| -------------------- |
    | **Definition**                 | Istio is an open platform for providing a uniform way to integrate microservices, manage traffic flow across microservices, enforce policies and aggregate telemetry data |
    | **Pros**                       | Flexible |
    | **Cons**                       | Performance |
    | **URL**                        | https://istio.io/ |

    | **Name**                       | Grafana              |
    | -------------------------------| -------------------- |
    | **Definition**                 | General purpose dashboard and graph composer |
    | **Pros**                       | Open source, interactive graphs, nice interface |
    | **Cons**                       |  |
    | **URL**                        | https://grafana.com/ |

    | **Name**                       | Prometheus           |
    | -------------------------------| -------------------- |
    | **Definition**                 | Prometheus is a systems and service monitoring system |
    | **Pros**                       | Open source, multi-dimensional data model, flexible query-language |
    | **Cons**                       | Only used for metrics |
    | **URL**                        | https://prometheus.io/ |

### 4.5.6 User Interface (UI)

The solution needs to implement front-end microservices with a light and user-friendly UI that is high on performance.

**Recommended technology**

| **Name**                       | React |
| -------------------------------| -------------------- |
| **Definition**                 | React is a JavaScript library for building modern single-page applications of any size and scale |
| **Pros**                       | Most popular framework for front-end, fast, simple design and easy to learn |
| **Cons**                       | Medium learning curve, assumes knowledge of JFX |
| **URL**                        | https://reactjs.org/ |

??? "Other alternatives"

    | **Name**                       | Angular |
    | -------------------------------| -------------------- |
    | **Definition**                 | Angular is a JavaScript MVVM framework used alongside with Typescript for building highly interactive web applications |
    | **Pros**                       | Angular-language-service that allows intelligence and autocomplete, detailed documentation, MVVM (Model-View-ViewModel) that allows separate work on same section |
    | **Cons**                       | Slower performance according to benchmarks, steep learning curve |
    | **URL**                        | https://angular.io/ |

    | **Name**                       | Vue |
    | -------------------------------| -------------------- |
    | **Definition**                 | Vue.js is a JavaScript framework for creating highly adaptable user interfaces and sophisticated Single-page applications |
    | **Pros**                       | Shallow learning curve, adaptability and large scaling through reusable templates |
    | **Cons**                       | Risk of over flexibility when integrating into big projects|
    | **URL**                        | https://vuejs.org/ |

### 4.5.7 Messaging

The solution needs a messaging service that provides fast guaranteed asynchronous message delivery when processing events.

**Recommended technology**

| **Name**                       | IBM Event Streams on IBM Cloud            |
| -------------------------------| -------------------- |
| **Definition**                 | IBM® Event Streams for IBM Cloud™ is a high-throughput message bus built with Apache Kafka |
| **Pros**                       | Fully Managed Apache Kafka Service. Geo-replication of topics between clusters to support high availability and scalability. Award-winning user experience. Highly Available and Resilient.|
| **Cons**                       |   |
| **URL**                        | https://cloud.ibm.com/docs/EventStreams/index.html |

??? "Other alternatives"

    | **Name**                       | Apache KafKa                |
    | -------------------------------| -------------------- |
    | **Definition**                 | Distributed, fault tolerant, high throughput pub-sub messaging system. RabbitMQ follows a protocol called AMQP (Advanced Message Queueing Protocol) |
    | **Pros**                       | Open source, High throughput, distributed and scalable.  |
    | **Cons**                       | Require several resources. Complicated UI |
    | **URL**                        | https://kafka.apache.org/ |


    | **Name**                       | Rabbit MQ             |
    | -------------------------------| -------------------- |
    | **Definition**                 | RabbitMQ is a general purpose message broker that supports protocols including, MQTT, AMQP, and STOMP. |
    | **Pros**                       | In Rabbit MQ, you can specify message priorities, and consumed message with high priority at the onset.  |
    | **Cons**                       | Not support messaging ordering |
    | **URL**                        | https://www.rabbitmq.com/ |


    | **Name**                       | MQ                   |
    | -------------------------------| -------------------- |
    | **Definition**                 | Enterprise-grade messaging middleware |
    | **Pros**                       | Useful for big enterprises, secure, stable, high availability and session recovery |
    | **Cons**                       | Limitation of volumes handled and message size, no embedded monitoring feature |
    | **URL**                        | https://www.ibm.com/support/knowledgecenter/SSFKSJ_9.0.0/com.ibm.mq.pro.doc/q001020_.htm |

### 4.5.8 Code quality

Code Quality controls can help reduce technical debt and increase security.

**Recommended technology**

| **Name**                       | SonarQube            |
| -------------------------------| -------------------- |
| **Definition**                 | Continuous inspection of code quality to perform automatic reviews with static analysis of code to detect bugs, code smells, and security vulnerabilities on 20+ programming languages. |
| **Pros**                       | Open Source Software. Possibility of setting multiple quality profiles. |
| **Cons**                       |   |
| **URL**                        | https://www.sonarqube.org/ |

??? "Other alternatives"

    | **Name**                       | Codacy               |
    | -------------------------------| -------------------- |
    | **Definition**                 | Automatically reviews code style, security, duplication, complexity, and coverage on every change while tracking code quality. |
    | **Pros**                       | Support for all major languages. Intuitive UI and easy dashboard give a clear display of your codebase. |
    | **Cons**                       |   |
    | **URL**                        | https://www.codacy.com/ |

### 4.5.9 Integration

The solution needs to expose its microservices and enable interaction between different modules as well as external systems.

**Recommended technology**

| **Name**                       | APIConnect |
| -------------------------------| -------------------- |
| **Definition**                 | IBM API Connect is a complete, intuitive and scalable API platform that lets you create, securely expose, manage and monetize APIs across clouds. |
| **Pros**                       | Smooth learning curve, secure and reliable gateway, analytics |
| **Cons**                       | Consume some resources from cluster to operate |
| **URL**                        | https://reprints2.forrester.com/#/assets/2/73/RES159081/report |

??? "Other alternatives"

    | **Name**                       | Apigee |
    | -------------------------------| -------------------- |
    | **Definition**                 | Apigee, part of Google Cloud, is a platform leading companies design, secure, and scale application programming interfaces (APIs) |
    | **Pros**                       | Predictive analytics, secure, easy-to-use |
    | **Cons**                       | Not cost-attractive |
    | **URL**                        | https://cloud.google.com/apigee |

### 4.5.10 Backend Microservices Framework

The solution needs a framework to develop business rules into microservices

**Recommended technology**

| **Name**                       | Open Liberty Eclipse Microprofile |
| -------------------------------| -------------------- |
| **Definition**                 | Eclipse MicroProfile is a modular set of technologies designed so that you can write cloud-native Java™ microservices. MicroProfile enables you to develop and deploy cloud-native Java applications as loosely coupled, lightweight services, each representing one unique business function. |
| **Pros**                       | Lightweight runtime. Fast startup. Smooth learning curve.  |
| **Cons**                       | Not as widely used as Spring boot |
| **URL**                        | https://projects.eclipse.org/proposals/eclipse-microprofile |

??? "Other alternatives"

    | **Name**                       | Quarkus |
    | -------------------------------| -------------------- |
    | **Definition**                 | Quarkus is a full-stack, Kubernetes-native Java framework made for Java virtual machines (JVMs) and native compilation, optimizing Java specifically for containers and enabling it to become an effective platform for serverless, cloud, and Kubernetes environments. |
    | **Pros**                       | Lightweight runtime. Fast startup.  |
    | **Cons**                       | Not as widely used as Spring boot or Eclipse Microprofile |
    | **URL**                        | https://quarkus.io/ |

    | **Name**                       | Eclipse Vert.x |
    | -------------------------------| -------------------- |
    | **Definition**                 | Eclipse Vert.x is a tool-​kit for build­ing re­active ap­pli­cations on the JVM. Re­ac­tive ap­pli­ca­tions are both scal­able as work­loads grow, and re­silient when fail­ures arise. |
    | **Pros**                       | Lightweight runtime. Fast startup.  |
    | **Cons**                       | Not as widely used as Spring boot or Eclipse Microprofile |
    | **URL**                        | https://vertx.io/ |

    | **Name**                       | Spring boot |
    | -------------------------------| -------------------- |
    | **Definition**                 | Spring Boot is an open source Java-based framework used to create a micro Service. It is developed by Pivotal Team and is used to build stand-alone and production ready spring applications. |
    | **Pros**                       | Widely used. Many add-ons.  |
    | **Cons**                       | Not as free as other alternatives. Not as efficient as Eclipse Microprofile or Eclipse Vert.x. |
    | **URL**                        | https://spring.io/projects/spring-boot |

    | **Name**                       | Node JS |
    | -------------------------------| -------------------- |
    | **Definition**                 | Node.js® is a JavaScript runtime built on Chrome's V8 JavaScript engine. |
    | **Pros**                       | Widely used. Lighter than Java-based components.  |
    | **Cons**                       | It requires understanding of JavaScript language and best practices. |
    | **URL**                        | https://nodejs.org/en/ |

### 4.5.11 Relational Database technology

The solution needs a technology to persist relational data on each microservice

**Recommended technology**

| **Name**                       | PostgreSQL |
| -------------------------------| -------------------- |
| **Definition**                 | PostgreSQL, also known as Postgres, is a free and open-source relational database management system emphasizing extensibility and SQL compliance. |
| **Pros**                       | Easy to use. Has a user-defined data type. Open-source. Make use of Stored procedures. It supports ACID: Atomicity, Consistency, Isolation, Durability. |
| **Cons**                       | No columnar tables. No machine learning included. |
| **URL**                        | https://cloud.ibm.com/catalog/services/databases-for-postgresql |

??? "Other alternatives"

    | **Name**                       | MySQL |
    | -------------------------------| -------------------- |
    | **Definition**                 | MySQL is an open-source relational database management system. Its name is a combination of "My", the name of co-founder Michael Widenius's daughter, and "SQL", the abbreviation for Structured Query Language. |
    | **Pros**                       | Easy to use. Open-source. Make use of Stored procedures. It supports ACID: Atomicity, Consistency, Isolation, Durability. |
    | **Cons**                       | MySQL is not as mature as other relational database management systems. MySQL is Oracle-owned instead of community driven. |
    | **URL**                        | https://www.mysql.com/ |

    | **Name**                       | MariaDB |
    | -------------------------------| -------------------- |
    | **Definition**                 | MariaDB is a community-developed, commercially supported fork of the MySQL relational database management system, intended to remain free and open-source software under the GNU General Public License. |
    | **Pros**                       | Easy to use. Open-source. Make use of Stored procedures. It supports ACID: Atomicity, Consistency, Isolation, Durability. |
    | **Cons**                       | MariaDB is liable to bloating. Its central IDX log file, in particular, tends to become very large after protracted use, ultimately slowing performance. Caching is another area where MariaDB could use work—it is not as fast as it could be, which can be frustrating. |
    | **URL**                        | https://mariadb.org/ |

### 4.5.12 NoSQL/Document Database technology

The solution needs a technology to persist Document-based data on each microservice

**Recommended technology**

| **Name**                       | MongoDB |
| -------------------------------| -------------------- |
| **Definition**                 | MongoDB is a source-available cross-platform document-oriented database program. Classified as a NoSQL database program, MongoDB uses JSON-like documents. |
| **Pros**                       | By storing a majority of the data in RAM, query performance in MongoDB is much quicker. Because of its expressive query language, many users find MongoDB query syntax to be rather simple and much easier to understand than SQL. As opposed to SQL databases that utilize vertical scalability, MongoDB (like other NoSQL databases) uses shards for horizontal scalability, which makes it easier to increase storage capacity. |
| **Cons**                       | Joining documents in MongoDB is no easy task. Atomic operations are supported at a single document level.  |
| **URL**                        | https://cloud.ibm.com/catalog/services/databases-for-mongodb |

??? "Other alternatives"

    | **Name**                       | CouchDB/Cloudant |
    | -------------------------------| -------------------- |
    | **Definition**                 | Apache CouchDB is an open-source document-oriented NoSQL database, implemented in Erlang. CouchDB uses JSON to store data. Cloudant is based on the Apache-backed CouchDB project.  |
    | **Pros**                       | Technically easy to use and integrate. REST API allows CouchDB to work with other technologies quickly. Using map/reduce allows to quickly implement new views of data.  |
    | **Cons**                       | Slower than in-memory DBMS. In-place updates require server-side logic (update handlers).  |
    | **URL**                        | https://cloud.ibm.com/catalog/services/cloudant |

    | **Name**                       | Cassandra |
    | -------------------------------| -------------------- |
    | **Definition**                 | Apache Cassandra is a free and open-source, distributed, wide column store, NoSQL database management system designed to handle large amounts of data across many commodity servers, providing high availability with no single point of failure. |
    | **Pros**                       | Flexible schema. Highly scalable and highly available with no single point of failure. Very high write throughput and good read throughput.  |
    | **Cons**                       | Cassandra does not support aggregates, if you need to do a lot of them, think another database. No join or subquery support. |
    | **URL**                        | https://cassandra.apache.org/ |

### 4.5.13 CI/CD technology

The solution needs a technology to manage Continuous Integration and Continuous Delivery pipelines

**Recommended technology**

| **Name**                       | DevOps Toolchain |
| -------------------------------| -------------------- |
| **Definition**                 | A DevOps toolchain is a set of self-managed tool integrations that support development, deployment, and operations tasks. The collective power of a toolchain is greater than the sum of its individual tool integrations. |
| **Pros**                       | Self-managed integrations and tools. Many tools available. Posibility to create complex integration and deployment pipelines. |
| **Cons**                       | It requires configuring a worker service to integrate with on-prem isolated services. |
| **URL**                        | https://www.ibm.com/cloud/architecture/toolchains/ |

| **Name**                       | ArgoCD |
| -------------------------------| -------------------- |
| **Definition**                 | Declarative, GitOps continuous delivery tool for Kubernetes |
| **Pros**                       | It compares the actual state of the application in the cluster with the desired state defined in Git and determines if they are out of sync. When it detects the environment is out of sync, Argo CD can be configured to either send out a notification to kick off a separate reconciliation process or Argo CD can automatically synchronize the environments to ensure they match. |
| **Cons**                       | It needs a Kubernetes or OpenShift environment to run in. |
| **URL**                        | https://argoproj.github.io/argo-cd/ |

??? "Other alternatives"

    | **Name**                       | Tekton |
    | -------------------------------| -------------------- |
    | **Definition**                 | The Tekton Pipelines project provides Kubernetes-style resources for declaring CI/CD-style pipelines. |
    | **Pros**                       | Tekton Pipelines are Decoupled: One Pipeline can be used to deploy to any Kubernetes cluster. The Tasks which make up a Pipeline can easily be run in isolation. Resources such as git repos can easily be swapped between runs |
    | **Cons**                       | It needs a Kubernetes or OpenShift environment to run in. |
    | **URL**                        | https://github.com/tektoncd/pipeline |

    | **Name**                       | Bamboo |
    | -------------------------------| -------------------- |
    | **Definition**                 | Atlassian Bamboo is a continuous integration (CI) and continuous delivery (CD) server. Bamboo assists software development teams by providing: automated building and testing of software source-code status. |
    | **Pros**                       | Bamboo, Bitbucket, and JIRA Software are fully integrated and give us full traceability from the time a feature request is made all the way to deployment. |
    | **Cons**                       | It needs an on-prem environment to run in. |
    | **URL**                        | https://www.atlassian.com/software/bamboo |

    | **Name**                       | Jenkins |
    | -------------------------------| -------------------- |
    | **Definition**                 | Jenkins is a free and open source automation server. It helps automate the parts of software development related to building, testing, and deploying, facilitating continuous integration and continuous delivery. It is a server-based system that runs in servlet containers such as Apache Tomcat. |
    | **Pros**                       | Open source automation server, Jenkins provides hundreds of plugins to support building, deploying and automating any project. |
    | **Cons**                       | It needs an on-prem environment to run in. |
    | **URL**                        | https://www.jenkins.io/ |

### 4.5.14 Code Repository

The solution needs a technology to track changes on code

**Recommended technology**

| **Name**                       | Bitbucket |
| -------------------------------| -------------------- |
| **Definition**                 | Bitbucket is a Git-based source code repository hosting service and on-premise appliance owned by Atlassian. |
| **Pros**                       | Integrates with the Atlassian suite. |
| **Cons**                       | Not open source. Can be pricey. Needs the Atlassian's suite to have all its competitors' features. |
| **URL**                        | https://bitbucket.org/ |

??? "Other alternatives"

    | **Name**                       | GitLab |
    | -------------------------------| -------------------- |
    | **Definition**                 | GitLab is an open-source web-based DevOps lifecycle tool that provides a Git-repository manager providing wiki, issue-tracking and continuous integration and deployment pipeline features. |
    | **Pros**                       | Open source. On top of VCS, has project management features along with pipelines. |
    | **Cons**                       | The UI can sometimes be unintuitive. |
    | **URL**                        | https://gitlab.com |

    | **Name**                       | GitHub |
    | -------------------------------| -------------------- |
    | **Definition**                 | GitHub brings to Git-based source code repositories a social network features that revolve around code. |
    | **Pros**                       | Many features on top of Git repository management: project management, actions (pipelines), webhooks, Pages (static website hosting), Gists (code snippets hosting), Wiki... |
    | **Cons**                       | Not open source. Can be pricey. |
    | **URL**                        | https://github.com/ |

### 4.5.15 Docker Image Storage Service

The solution needs a technology to store Built docker images of deployed microservices

**Recommended technology**

| **Name**                       | IBM Cloud Container Registry |
| -------------------------------| -------------------- |
| **Definition**                 | Store and distribute container images in a fully managed private registry. Push private images to conveniently run them in the IBM Cloud® Kubernetes Service and other runtime environments. Images are checked for security issues so you can make informed decisions about your deployments. |
| **Pros**                       | Features image vulnerability scanning, robust access controls, and a web-based UI. |
| **Cons**                       | Not open source. |
| **URL**                        | https://cloud.ibm.com/registry/catalog |

??? "Other alternatives"

    | **Name**                       | Quay.io |
    | -------------------------------| -------------------- |
    | **Definition**                 | Online or self-hosted private Docker image repository maintained by Red Hat. |
    | **Pros**                       | Open source. Features image vulnerability scanning, robust access controls, and a web-based UI. |
    | **Cons**                       | Self-hosted version needs managing it. |
    | **URL**                        | https://quay.io/ |

    | **Name**                       | OpenShift Image Registry |
    | -------------------------------| -------------------- |
    | **Definition**                 | OpenShift provides a built-in container image registry that runs as a standard workload on the cluster. |
    | **Pros**                       | Integrated into the cluster user authentication and authorization system. |
    | **Cons**                       | No web-based UI. |
    | **URL**                        | https://docs.openshift.com/container-platform/4.6/registry/architecture-component-imageregistry.html |


### 4.5.16 Micro-services contract testing

The solution needs a technology to check the contracts among microservices

**Recommended technology**

| **Name**                       | Pact |
| -------------------------------| -------------------- |
| **Definition**                 | Pact automates contract testing and enables it to be added to a continuous integration pipeline |
| **Pros**                       | Available for different languages. It's opensource|
| **Cons**                       | |
| **URL**                        | https://docs.pact.io/ |

??? "Other alternatives"

    | **Name**                       | IBM Rational Integration tester |
    | -------------------------------| -------------------- |
    | **Definition**                 | Rational® Integration Tester is an integration testing and virtualization tool that includes capabilities to automate and run tests earlier and more often to find problems sooner in the development cycle.|
    | **Pros**                       | It has a technology to stub/mock services through proxy. No need to write code |
    | **Cons**                       | It's not free |
    | **URL**                        | https://help.blueproddoc.com/rationaltest/rationalintegrationtester/10.1.2/index.html |

    | **Name**                       | Spring Cloud Contract |
    | -------------------------------| -------------------- |
    | **Definition**                 | Spring cloud contract has focusing on consumer testing |
    | **Pros**                       | |
    | **Cons**                       | Only avaiable using Spring|
    | **URL**                        | https://spring.io/projects/spring-cloud-contract |

    | **Name**                       | Hoverfly |
    | -------------------------------| -------------------- |
    | **Definition**                 | Hoverfly can be used for testing REST APIs as well as testing calls between microservices |
    | **Pros**                       | Lightweight, high-performance, run anywhere |
    | **Cons**                       | |
    | **URL**                        | https://hoverfly.io/ |



### 4.5.17 End to end testing

The solution needs a technology to check End to End scenarios for Behavior Driven Testing

**Recommended technology**

| **Name**                       | Cypress |
| -------------------------------| -------------------- |
| **Definition**                 | Cypress is a free and opensource testing tool written in Javascript|
| **Pros**                       | Cypress is a more developer-friendly tool that uses a unique DOM manipulation technique and operates directly in the browser. Cypress also provides a unique interactive test runner in which it executes all commands. |
| **Cons**                       | Cypress only supports JavaScript for creating test cases |
| **URL**                        | https://www.cypress.io/|

??? "Other alternatives"

    | **Name**                       | Selenium |
    | -------------------------------| -------------------- |
    | **Definition**                 | Selenium is a web ui testing tool based on a WebDriver|
    | **Pros**                       | It can be used with different languages: Java, Python, C#, Rubu, Javascript, Kotlin |
    | **Cons**                       | Creating test cases is time-consuming.  |
    | **URL**                        | https://help.blueproddoc.com/rationaltest/rationalintegrationtester/10.1.2/index.html |

    | **Name**                       | IBM Rational Functional Tester |
    | -------------------------------| -------------------- |
    | **Definition**                 | IBM Rational® Functional Tester is a commercial testing tool able to test old-fashioned applications and new spa application.|
    | **Pros**                       | It can test desktop application and web ui|
    | **Cons**                       | It's not free |
    | **URL**                        | https://help.blueproddoc.com/rationaltest/rationalfunctionaltester/10.1.2/index.html|


### 4.5.18 Artifacts Persistency

The solution needs a technology to persist Artifacts for development (I.E.: Maven libraries, NPM Modules)

**Recommended technology**

| **Name**                       | Sonatype Nexus Repository|
| -------------------------------| -------------------- |
| **Definition**                 | Nexus is an artifact management repository.
| **Pros**                       | The opensource version (Nexus Repository OSS) supports a wide range of repositories: Docker, Maven, NuGet, npm, Go, PyPI, yum, apt, p2, helm |
| **Cons**                       | Less features than Artifactory  |
| **URL**                        | https://www.sonatype.com/nexus/repository-oss |


??? "Other alternatives"

    | **Name**                       | Artifactory |
    | -------------------------------| -------------------- |
    | **Definition**                 | Artifactory is an artifact management repository.
    | **Pros**                       | Artifactory has more features compared with the the other two |
    | **Cons**                       | The opensource version (Artifactory OSS) supports only Maven, Gradle and Ivy |
    | **URL**                        | https://jfrog.com/artifactory/ |

    | **Name**                       | Verdaccio |
    | -------------------------------| -------------------- |
    | **Definition**                 | Verdaccio is a lightweight open source private npm proxy registry
    | **Pros**                       | It is completely opensource |
    | **Cons**                       | npm support only |
    | **URL**                        | https://verdaccio.org/ |

