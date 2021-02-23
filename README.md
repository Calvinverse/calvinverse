# Calvinverse

Provides a the tools and services to to create and configure environments for an application or
service in a repeatable manner.

  > An **environment** is a collection of resource instances and services that work together
  > to achieve one or more goals, e.g. to provide the ability to serve customers with
  > the ability to create, edit and store notes.

* Sometimes it would be useful if you could quickly create an environment from scratch and potentially
  destroy it again when you are done with it. For instance if you want to test some changes, or if
  you want to have another production environment in a different geographic region
* The problem is that creating an environment from scratch is hard. It often involves creating different
  resources (container instances, load balancers, event systems, service discovery, configuration storage,
  data storage etc.) as well as configuring these systems, providing valid certificates, DNS names,
  securing the resources, setting up configurations etc. etc. etc.
* In general creating the resources is a problem solved by many different tools, e.g. terraform or
  one of the orchestration systems (docker, kubernetes etc.). But introducing secrets, certificates
  and configurations isn't always easy. This often involves different tools to handle these tasks
  in a safe and secure manner
* Destroying environments is usually handled by the tools, but needs to be instigated by a user,
  who might forget.
* Keeping environments up to date due to changes in the services / configurations / secrets
* Updating to newer versions. Simple for a new application version, but often comes with
  updates to configs and secrets

Calvinverse provides services / tools to resolve some of these issues

* Born because I wanted a way to create test environments, easily

## What is in the box

* Two services
  * UI
  * Provisioning service
* Definitions for data etc.
* Scripts / tooling to create a meta-environment that will contain the two services
  (bootstrap)

## Examples
