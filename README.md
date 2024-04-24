# Spring_Boot_Microservices_Tutorial
Following a YT tutorial on Spring boot Microservices 
YT Link: https://www.youtube.com/watch?v=mPPhcU7oWDU&t=6s



# Microservices Info

YT Links:
https://www.youtube.com/watch?v=lTAcCNbJ7KE
https://www.youtube.com/watch?v=lL_j7ilk7rc
https://www.youtube.com/watch?v=rv4LlmLmVWk

## 1. Vid
Microservices are coupled services, with each providing only a small amount of functions, used to together to perform as one big System/program.

Microservices can also be called domains.
These domains can communicated/interact with each other over small and well managed interfaces, called surface areas, in order to keep possible errors and the following damage to a minimum

They communicate via RPC (Remote Procedure Calls), Event Streaming or Message brokers
	RPCs/gRPCs: are faster but also have a bigger impact if one of the services would go down
	Event streaming: Provide better isolation between services but takes longer to process

With microservices being smaller, easier to configure and a smaller damage radius it allows for easier development and more frequent deployment. They provide more flexibility for scaling themselves independently. 

They as well allow and support the splitting of a monolithic data base in its core logical component and hiding those inside the different services.

A negative aspect of Microservices is that by splitting the main database in its core parts the ability of keeping forgone key relationships is lost and moved to the application layer.

The parts needed for implementing this kind of architecture are obviously the services and to those fitting database pieces but the main part is the API Gateway which routes the Clients request to the needed services. It does that, on one hand, by using an Identity Provider Service, with which it authenticates and authorises every request that comes through the Gateway and on the other hand a Service Registry & Discovery Service with which the API and the microservices register and discover other microservices.
There are also other parts like monitoring, alerting as well as diffrent dev tools.

Microservices are most plausible for bigger teams or companies as they are expensive to create and need a lot of personal to operate/maintain. With a big number of people you can give teams independency to maintain, develop and fix every domain on their own with minimal damage risk. 
Its not recomended for startups and should be used after the startup has grown a bit


## 2. Vid
### Monolithic
It's straight forward, only one big piece of code with all the Data, business logic and UI

### Multitier
or also called multi-layered, splitting the code up in different parts/layers. In the 3 Tiers Architecture it would be "Data Layer"(Data), "Logic Layer" (Business Logic) and "Presentation Layer" UI. 

By time programs and projects have become quite complex and with that need higher maintains, more evolvement and being scaled for the size of the project.
That can be done by breaking the Multitier system in even smaller parts, now making 3 layers for each business function. Those parts are connected via APIs and communicated with protocols like HTTP or Message ques. 
With the functions being split apart teams can work on them more easily without risking creating problems in other parts of the application. 
It allows even the use of different programming languages between services but in order to keep the cost down, improve efficiency and optimize operations the company or teams should decide to limit the use of tools, infrastructure provider and programming languages.
As a project grows and gains on services as well as complexity the risk of creating a cascade of outages as a reaction of one service failing grows too. And because of the sheer amount of services the time needed to find and resolve those problems increase on top of all that.
As a reaction to that problem the programming community has developed different tools in order to tackle different aspects of the problem:
	- Containerization/docker: deploying services in minimalistic self-contained runtimes 
	- Container Orchestration/kubernetes: Managing container lifecycles 
	- Pipeline Automation/Git Lab: for CI/CD
	- Asynchronous Messaging/kafka: further decoupling of services by providing message brokers and views
	- Performance Monitoring/Prometheus: to track performance of services
	- Logging and Audit/DataDog: keeping track and having an eye on everything that goes on in the services


## 3. Vid

#### Monolith
- one single unit
- developed deployed and scaled as 1 unit
- 1 tech stack / 1 programming language / 1 runtime
- Teams need to be careful not to interfere with each others code/work
- When updating a single thing the entire thing needs to be redeployed

##### Negatives
- The application is too large and complex to understand efficiently
- Each part or function is more tangled into each  other making it hard to work on individual parts
- The only way to scale the app is to double the entire thing
- Dependencies can only be imported once resulting in problems when different parts need different versions of the same dependency
- Release process takes longer as it is one giant app
- One every change, the entire application needs to be tested as it is so intertangled 
- entire application needs to be built and deployed not just the needed parts
- A bug in one feature can possible bring down the entire app

#### Microservices

##### Questions
- How to break down the application? 
	-> business functionalities -> 1 service = 1 specific job -> self-contained & independent
- What codes goes where? -> 
- How many services do we create?
- How big/small should they be?
- How do they communicate?
	-> API calls -> HTTP Request/Responses between the services aka Synchronous communication 
	-> Message Broker -> via messages send first to a message broker, with the given destination being contained in the message as well, who know where the other services are 
	-> Service mesh -> a helper service (network layer) which takes the places as the communicator between services

#### Pros
- Own techstack for each microservice
- each team can work on their part without affecting other parts of the code

#### Cons
- Communication between services needs to be set up and work properly 
- it's harder to monitor and find problems across so many systems

#### Tools
- Kubernetes: for running large microservice applications 

#### CI/CD pipeline
- knowing how and how often the services and their parts are being deployed

#### Code management for microservices
2 Options
Monorepo
Pro
- Using Folders
- easier management and development
- clone and work only with 1 repo
- changes can be tracked, tested and released together
- sharable code and configs
Cons
- tight connections between code can easily lead to a fuck up 
- its easier to write such tightly coupled code
- big projects lead to big amounts of code leading to slow git interactions
- Additional logic necessary to only changed services are build and deployed
- if one branch/part has a problem all parts have
Polyrepo
Pro
- Code is completely isolated
- clone and work on them separately
- GitLab Groups allow grouping of those multiple repos
- one pipeline for each repo
Cons
- changing things in multiple repos is harder
- Changes across projects need to be submitted as separate Merge requests
- Switching between projects is tedious
- Searching, testing and debugging is more difficult
- sharing resources is more difficult

Mono -> Small
Poly -> Big


