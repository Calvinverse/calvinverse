# Domain

The domain in which the Calvinverse resources operate is that of environments for SaaS services. The different [domain models](https://en.wikipedia.org/wiki/Domain_model) are

* Environment
* Service
* Resource
* Application
* Artefact
* Deployment
* Template
* User
* User group

## Environment

An **environment** is the collection of exclusive resources, services and data that work together
to achieve one or more goals, e.g. to allow users to achieve their tasks.

Each environment has a unique purpose for existing, e.g. a test environment or a
production environment in a specific geographic region. Environments that share a purpose
are generally not independent, i.e. they share data or services, which means that changes to one
environment may affect the connected environments.

An environment is generally identified by a name and has the following properties:

* **name** - The name of the environment. Used to distinguish different environments from each other.
  For instance `production` or `development`.
* **resources** - The collection of different resources that define what the environment is
  capable of.


## Service

According to [Wikipedia](https://en.wikipedia.org/wiki/Service_(systems_architecture)) a **service**
refers to a software functionality or a set of software functionalities with a purpose that
different clients can reuse for different purposes, together with the policies that should control
its usage (based on the identity of the client requesting the service, for example).

In general there is only one service that provides a given functionality in a specific environment,
although multiple versions of the same service may be present in that environment. The functionality
for a service is provided by one or more resources and applications. While there will generally only
be one 'instance' of a service there may be multiple instances of the resources or applications that
provide the service functionality.

A service is generally identified by a name and a version and has the following properties:

* **name** - The name of the service. Used to distinguish different services from each other.
* **version** - The version of the service.


* Endpoints / communication mechanism?

## Resource

A **resource** is an instance of an infrastructure element, e.g. a virtual machine, docker container,
network etc.. The resource may represent a physical or virtual element.

Resources are identified by an ID and have the following properties:

* **ID** - The identifier for the resource.
* **name** - The name of the resource
* **type** - The type of the resource, e.g. virtual machine, network etc.

## Application

An **application** is a [collection of instructions](https://en.wikipedia.org/wiki/Computer_program)
which are executed to perform a specific task.

An application is identified by a name and a version. It has the following properties:

* **name** - The name of the application.
* **version** - The version of the application

## Artefact

An **artefact** is an output of the software development process.

Artefacts are identified by their name and version. They have the following properties:

* **name** - The name of the artefact.
* **version** - The version of the artefact. For some artefacts re-creating the artefact from the
  original inputs will lead to a different artefact with a (slightly) different version.
* **date of creation** - The date on which the artefact was created.
* **input references** - References to the inputs that were used to create the artefact, e.g.
  the source control ID and names of any other artefacts that are part of the current artefact.

## Deployment

A **deployment** is the collection of actions necessary to transfer and activate a new version
of a resource, service or application to an environment.

Deployments are identified by their ID and have the following properties:

* **ID** - The ID of the deployment.

* TODO: What is the term for the deployment template, i.e. the things that will be done when
  a deployment is executed.
* Deployments are immutable and can only be done once. Even when an identical set of applications
  / services is deployed to the same environment it is a new deployment



## Release

* TODO: Do we need this?
* A release is marking a version of an application, service or environment as complete and allowed
  to be used by customers / users
* Different from a deployment, which is actually activating the application / service / environment

* Release is a metadata thing, deployment is a 'physical' thing




## Template

* Template for what? Different templates exist
  * deployment
  * Environments
  * Services
* Actually templates are always for the deployment that creates the thing
  * How does that work with e.g. Terraform files, essentially those are templates

## User

A **user** is a representation of an entity that needs permissions to interact with some or all of
the parts of the environment.

* **Name** - The name of the user.
* **Groups** - The groups the user belongs to.

## User group

A **user group** is a collection containing users. In general the purpose of a **user group** is
to assign permissions to abstract assigning user permissions to groups of users.

* **Name** - The name of the group.
* **Users** - The users that belong to this group.

## Data / Configuration

??

* Secrets
* Config
* Certificates
* Data imports / migration / ownership / relinking