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

* Two services
  * UI
  * Provisioning service
* Definitions for data etc.
* Scripts / tooling to create a meta-environment that will contain the two services
  (bootstrap)

## Examples
