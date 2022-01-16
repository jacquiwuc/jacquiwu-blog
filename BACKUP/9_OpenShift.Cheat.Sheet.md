# [OpenShift Cheat Sheet](https://github.com/jacquiwuc/jacquiwu-blog/issues/9)

### What is Openshift?

OpenShift is Red Hat's Platform as a Service(PaaS) that allows developers to quickly develop, host and scale applications in a cloud environment. Openshift makes use of the Kubernetes upstream project to provide a secure, robust and extendable manner for orchestrating applications. Openshift works to further the access management and build/deploy services that are provided in the upstream Kubernetes project. Development teams are empowered to own and maintain their applications through production environments, while operations teams can provide guide rails for developers to have the application ownership in a multi-tenant environment.

### Command Overview
Login/User management
| Command      | Description |
| ----------- | ----------- |
| oc login      | authenticate to an openshift cluster       |
| oc logout   | end the current session        |
| oc whoami   | show the current user context        |