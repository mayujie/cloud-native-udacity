# cloud-native-udacity
This repository is containing notes and tutorials from Cloud Native Fundamentals Scholarship

# Introduction to Cloud Native Fundamentals

## 3. Course Outline

Summary

Throughout the course, we will walk through a realistic example of applying good development practices and containerizing an application, before it's released to a Kubernetes cluster using an automated CI/CD pipeline.

This course has the following lessons:

- Welcome
- Architecture Considerations
- Container Orchestration
- Open Source PaaS
- Cloud Native CI/CD 

In the first lesson, we will cover:

- Introduction to Cloud Native
- CNCF and Cloud Native tooling
- Stakeholders
- Tools, Environment & Dependencies

## 4. Introduction to Cloud Native
Summary

Cloud-native refers to the set of practices that empowers an organization to **build and manage applications at scale**. They can achieve this goal by using private, hybrid, or public cloud providers. In addition to scale, an organization needs to be agile in integrating customer feedback and adapting to the surrounding technology ecosystem.

**Containers** are closely associated with cloud-native terminology. Containers are used to run a single application with all required dependencies. The main characteristics of containers are easy to manage, deploy, and fast to recover. As such, often, a microservice-based architecture is chosen in tandem with cloud-native tooling. Microservices are used to manage and configure a collection of small, independent services that can be easily packaged and executed within a container.

## 5. CNCF and Cloud-Native Tooling
Summary

**Kubernetes** had its first initial release in 2014 and it derives from Borg, a Google open-source container orchestrator. Currently, Kubernetes is part of **CNCF** or **Cloud Native Computing Foundation**. CNCF was founded in 2015, and it provides a **vendor-neutral home to open-source projects** such as Kubernetes, Prometheus, ETCD, Envoy, and many more.

k8s automates configuration, management, scalability

Overall, Kubernetes is a container orchestrator that is capable to solutionize the integration of the following functionalities:

- Runtime
- Networking
- Storage
- Service Mesh
- Logs and metrics
- Tracing

## 6. Stakeholders
Summary

An engineering team can use cloud-native tooling to enable quick delivery of value to customers and easily extend to new features and technologies. These are the main reasons why an organization needs to adopt cloud-native technologies. However, when trialing cloud-native tooling, there are two main perspectives to address: business and technical stakeholders.

From a business perspective, the adoption of cloud-native tooling represents:

- Agility - perform strategic transformations
- Growth - quickly iterate on customer feedback
- Service availability - ensures the product is available to customers 24/7

From a technical perspective, the adoption of cloud-native tooling represents:

- Automation - release a service without human intervention
- Orchestration - introduce a container orchestrator to manage thousands of services with minimal effort
- Observability - ability to independently troubleshoot and debug each component

# Architecture Consideration for Cloud Native Applications

## 1. Introduction
Summary

Welcome to the Cloud Native Fundamentals course!

Before building an application, it is common to go through a design phase to identify the main requirements and structure of an application. In correlation with the available resources, a team will choose the most suitable project architecture.

In the industry, usually, the two main approaches that are usually referenced are monoliths and microservices. In this lesson, we will explore each architectural model and the implied trade-offs. As well, we will cover good development practices to be considered if an application is targeted for containerization. These practices are valid for both monolith and microservice architectures.

![ff](https://video.udacity-data.com/topher/2020/December/5fdd0741_screen-shot-2020-12-18-at-11.47.00-am/screen-shot-2020-12-18-at-11.47.00-am.png "Architecture Considerations lesson outline")

In this lesson, we will cover:

- Monoliths and Microservices
- Trade-offs for Monoliths and Microservices
- Practices for Application Development

## 2. Design Considerations for Cloud-Native Applications
Summary

When building an application it is important to allocate time for context discovery. This includes listing all necessary functionalities of the application and enumerating any resources that can enable its buildout. This phase sets the fundamentals of the project. If properly implemented, it can enable the creation of services that are scalable, resilient, and extensible.

The first step in the context discovery process is to list the functional requirements, or what application capabilities should deliver to the end-users. For example, a good starting point is to expand on the following:

- Stakeholders
- Functionalities
- End users
- Input and output process
- Engineering teams
- The second step is to enumerate the available resources that facilitates the implementation of the project. For example, a good starting point is to list available:

- Engineering resources
- Financial resources
- Timeframes
- Internal knowledge

Having a good understanding of functional requirements and available resources can lead to a simpler choice between monolithic and microservice-based architectures.

## 3. Monoliths and Microservices
Prior to an organization delivers a product, the engineering team needs to decide on the most suitable application architecture. In most of the cases 2 distinct models are referenced: monoliths and microservices. Regardless of the adopted structure, the main goal is to design an application that delivers value to customers and can be easily adjusted to accommodate new functionalities.

Also, each architecture encapsulates the 3 main tires of an application:
- UI (User Interface) - handles HTTP requests from the users and returns a response
- Business logic - contained the code that provides a service to the users
- Data layer - implements access and storage of data objects

Monoliths

In a monolithic architecture, application tiers can be described as:

- part of the same unit
- managed in a single repository
- sharing existing resources (e.g. CPU and memory)
- developed in one programming language
- released using a single binary

![alt text](https://video.udacity-data.com/topher/2020/December/5fdd2602_screenshot-2020-12-18-at-21.57.06/screenshot-2020-12-18-at-21.57.06.png "A booking application referencing the monolithic architecture")

Imagine a team develops a booking application using a monolithic approach. In this case, the UI is the website that the user interacts with. The business logic contains the code that provides the booking functionalities, such as search, booking, payment, and so on. These are written using one programming language (e.g. Java or Go) and stored in a single repository. The data layer contains functions that store and retrieve customer data. All of these components are managed as a unit, and the release is done using a single binary.

Microservices

In a microservice architecture, application tiers are managed independently, as different units. Each unit has the following characteristics:

- managed in a separate repository
- own allocated resources (e.g. CPU and memory)
- well-defined API (Application Programming Interface) for connection to other units
- implemented using the programming language of choice
- released using its own binary

![micro](https://video.udacity-data.com/topher/2020/December/5fdd26ac_screenshot-2020-12-18-at-22.01.07/screenshot-2020-12-18-at-22.01.07.png "A booking application referencing the microservice architecture")

Now, let's imagine the team develops a booking application using a microservice approach.

In this case, the UI remains the website that the user interacts with. However, the business logic is split into smaller, independent units, such as login, payment, confirmation, and many more. These units are stored in separate repositories and are written using the programming language of choice (e.g. Go for the payment service and Python for login service). To interact with other services, each unit exposes an API. And lastly, the data layer contains functions that store and retrieve customer and order data. As expected, each unit is released using its own binary.

New terms
- Monolith: application design where all application tiers are managed as a single unit
- Microservice: application design where application tiers are managed as independent, smaller units

Further reading
- [What’s the Difference Between Monolith and Microservices?](https://nordicapis.com/whats-the-difference-between-monolith-and-microservices/)
- [Microservices vs Monolithic Architecture](https://www.mulesoft.com/resources/api/microservices-vs-monolithic)


## 5. Trade-offs for Monoliths and Microservices
An application can be designed using both, monolithic or microservice-based architectures. So far, we have looked at how the structure of an application is contoured by functional requirements and available resources. However, each architecture has a set of trade-offs, that need to be thoroughly examined before deciding on the final structure of the application.

These trade-offs cover development complexity, scalability, time to deploy, flexibility, operational cost, and reliability. Let's examine each trade-off in more detail!

Summary

Development Complexity

Development complexity represents the effort required to deploy and manage an application.

- Monoliths - one programming language; one repository; enables sequential development
- Microservice - multiple programming languages; multiple repositories; enables concurrent development
Scalability
Scalability captures how an application is able to scales up and down, based on the incoming traffic.

- Monoliths - replication of the entire stack; hence it's heavy on resource consumption
- Microservice - replication of a single unit, providing on-demand consumption of resources

Time to Deploy

Time to deploy encapsulates the build of a delivery pipeline that is used to ship features.

- Monoliths - one delivery pipeline that deploys the entire stack; more risk with each deployment leading to a lower velocity rate
- Microservice - multiple delivery pipelines that deploy separate units; less risk with each deployment leading to a higher feature development rate

Flexibility

Flexibility implies the ability to adapt to new technologies and introduce new functionalities.

- Monoliths - low rate, since the entire application stack might need restructuring to incorporate new functionalities
- Microservice - high rate, since changing an independent unit is straightforward

Operational Cost

Operational cost represents the cost of necessary resources to release a product.

- Monoliths - low initial cost, since one code base and one pipeline should be managed. However, the cost increases exponentially when the application needs to operate at scale.
- Microservice - high initial cost, since multiple repositories and pipelines require management. However, at scale, the cost remains proportional to the consumed resources at that point in time.

Reliability

Reliability captures practices for an application to recover from failure and tools to monitor an application.

- Monoliths - in a failure scenario, the entire stack needs to be recovered. Also, the visibility into each functionality is low, since all the logs and metrics are aggregated together.
- Microservice - in a failure scenario, only the failed unit needs to be recovered. Also, there is high visibility into the logs and metrics for each unit.

Each application architecture has a set of trade-offs that need to be considered at the genesis of a project. But more importantly, it is paramount to understand how the application will be maintained in the future e.g. at scale, under load, supporting multiple releases a day, etc.

There is no "golden path" to design a product, but a good understanding of the trade-offs will provide a clear project roadmap. Regardless if a monolith or microservice architecture is chosen, as long as the project is coupled with an efficient delivery pipeline, the ability to adopt new technologies, and easily add features, the path to could-native deployment is certain.
## 8. Solution: Monoliths and Microservices
Given the scenario, it is paramount to choose an architecture that would be replicable and scalable. For example, if thousands of customers access the payment service in the same timeframe, then this particular service should be scaled up. In a monolith architecture, scaling up creates a replica of everything, including front-end and customer services, in addition to the payment service. This will also consume more resources on the platform, such as CPU and memory, and takes longer to spin up.

On the other side, a microservice is a lightweight component that requires fewer resources (CPU and memory) and less time for provisioning.

For this example, a microservice-based architecture is chosen, based on considerations that the application is a central booking system for multiple airlines, that implies a high load. The main components are:

- Front-end - entry-point for the user, where they will choose their airline or choice
- Customer - requires a database (MySQL or Mongo) to store the customer details
- Payments - to implement PayPal and Debit based operations

![sl](https://video.udacity-data.com/topher/2020/October/5f9af2f2_screenshot-2020-10-29-at-15.36.09/screenshot-2020-10-29-at-15.36.09.jpg "Flight booking application using microservice architecture")
Additionally, the "payments" microservice is capable of handling multiple payment systems. Interaction with the PayPal interface and management of debit card APIs are fundamentally different. The "payments" component is a monolith that can be divided into multiple parts.

Payments:

- PayPal - handling all the PayPal payments
- Debit - handling all the debit card payments

![sl1](https://video.udacity-data.com/topher/2020/October/5f9b33ae_screenshot-2020-10-29-at-15.36.18/screenshot-2020-10-29-at-15.36.18.png "Payment service being split into PayPal and Debit microservices")


[comment]: <> (![]&#40; ""&#41;)

# Container Orchestration with Kubernetes

# Open Source PaaS

# CI/CD with Cloud Native Tooling
