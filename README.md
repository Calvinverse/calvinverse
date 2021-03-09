# Calvinverse

Provides the tools and services to to create, configure and destroy environments for an application or
service in a repeatable manner.

  > An **environment** is the collection of exclusive resources, services and data that work together
  > to achieve one or more goals, e.g. to allow users to achieve their tasks.

## Why

In some cases it would be nice to be able to create an environment in repeatable way, for instance

* When running tests on a new feature or for performance. The ability to execute these in a fresh
  environment that matches the current production configuration reduces differences between the test
  and production.
* The ability to create a new environment in a different geographic region.

The problem is that creating an environment from scratch is hard. It often involves creating different
resources (container instances, load balancers, event systems, service discovery, configuration storage,
data storage etc.) as well as configuring these systems, providing valid certificates, DNS names,
securing the resources, setting up configurations etc..

## Why not use <insert favorite tool here>

The problem of creating, updating and deleting resources is solved by many different tools, e.g.
terraform or one of the orchestration systems (docker, Kubernetes etc.). But introducing secrets,
certificates and configurations isn't always easy. This often involves different tools to handle
these tasks in a safe and secure manner.

In cases where an environment needs to be destroyed after user it is often left to the user to initiate
the destroy action. However users may forget this leading to expensive resources going unused. Most
of the tools that are used to create resources aren't able to destroy the same resources on a
schedule or based on events.

The goal for Calvinverse is to provide a service that will use the well known tools to create,
update and destroy environments while adding the ability to inject configurations, certificates and
secrets.

## What is in the box

The Calvinverse resources can be divided into two groups. The first group contains the resources and
services necessary to create new environments. This environment is called the provisioning or
meta environment. The second group contains the resources that form
a build environment for the Calvinverse resources. This environment can be created if desired but
there are other ways to construct the services and resources in the first group.

### Meta environment

The meta environment contains the following services and resources

* A Dockerised service that provides a Web UI though which users can request
  creation, updating or deletion of environments. Additionally this UI provides an overview of
  all existing environments that a user has access to.
* A Dockerised service that processes user requests by invoking the appropriate tools, e.g.
  Terraform, to apply the requested changes. This service also tracks the current state of all the
  known environments. This service is known as the provisioning service.

In order to create the meta environment one can either use the configuration file for the orchestrator
of choice or the provisioning service locally and provide it with the desired environment configuration.
The benefit of the latter approach is that, with the appropriate templates, it is possible to create
the desired orchestrators prior to creation of the user environments.

### Calvinverse build environment

The build environment contains the services and resources required to create all the images necessary
for the meta environment.

This build environment may be used, however it is not required to do so if the meta environment
images can be created in another fashion.

### Environment requirements

* Assumes service discovery is done via Consul

## Examples
