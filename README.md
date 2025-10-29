# datagrid-config

![Version: 0.0.1](https://img.shields.io/badge/Version-0.0.1-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square) ![AppVersion: 8.5.12](https://img.shields.io/badge/AppVersion-8.5.12-informational?style=flat-square)

A Helm chart for configuring Red Hat Data Grid Instances using the Red Hat Data Grid Operator

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| authentication | object | See child keys | Control authentication configurations for Red Hat Data Grid |
| authentication.credentialsSecretName | string | `nil` | Name of the `Secret` containing an identities declaration used to configure a properties realm |
| authentication.disable | bool | `false` | Disable authentication. Not recommended for production. |
| authorization | object | See child keys | Control authorization for Red Hat Data Grid. |
| autoscaling | object | See child keys | Control autoscaling for Red Hat Data Grid. This should be disabled during upgrade procedures as it will interfere with the upgrade process. |
| availability | string | See child keys | Control high availability for Red Hat Data Grid. |
| caches | string | See child keys | Cache configuration for caches |
| credentialsStore | object | See child keys | Configuration of a `Secret` used to store sensitive information |
| credentialsStore.enabled | boolean | `false` | Use a `Secret` to store sensitive information such as credentials |
| credentialsStore.secretName | string | `nil` | The name of the `Secret` used to store sensitive information |
| customConfig | object | See child keys | Settings related to the Red Hat Data Grid Operator Cluster |
| customConfig.config | object | `nil` | The custom Red Hat Data Grid configuration |
| customConfig.enabled | boolean | `false` | Create a `ConfigMap` with a custom Red Hat Data Grid configuration |
| encryption | object | See child keys | Control encryption configurations for Red Hat Data Grid |
| encryption.disable | bool | `false` | Disable encryption. Not recommended for production. |
| expose | object | See child keys | Used to expose Red Hat Data Grid for external connections |
| expose.hostname | string | `nil` | A specific hostname used to expose Red Hat Data Grid when  `expose.type` is set to `Route` |
| expose.port | string | Defaults to `11222` when `expose.type` is set to `LoadBalancer` | The port number used to expose Red Hat Data Grid when `export.type` is set to `NodePort` or `LoadBalancer` |
| infinispan | object | See child keys | Settings related to the Red Hat Data Grid Operator Cluster |
| infinispan.disableConfigListener | bool | `false` | Disable the config listener pod. You should do this only if you do not  need declarative Kubernetes representations of Data Grid resources created through the Data Grid Console, CLI, or client applications.    |
| infinispan.enabled | boolean | `true` | Create a `Subscription` for the Red Hat Data Grid Operator |
| infinispan.name | string | `"datagrid"` | The name of the Red Hat Data Grid cluster |
| infinispan.replicas | int | `1` | The number of nodes that will form part of the Red Hat Data Grid cluster |
| infinispan.upgradeType | string | `"Shutdown"` | Used to control the behavior of Red Hat Data Grid version upgrades. |
| infinispan.version | string | `"8.5.3-1"` | The Red Hat Data Grid version to install.  Not to be confused with the Red Hat Data Grid Operator version. |
| logging | object | See child keys | Control log level for categories for Red Hat Data Grid. |
| monitoring | object | See child keys | Control monitoring configurations for Red Hat Data Grid |
| monitoring.disablePrometheus | bool | `false` | Disable the default prometheus service monitor |
| monitoring.enableJMX | bool | `false` | Enable JMX remote ports. This is not needed for prometheus endpoints. |
| operator | object | See child keys | Settings related to the Red Hat Data Grid Operator `Subscription` |
| operator.channel | string | `"stable"` | The `channel` of the Operator |
| operator.enabled | boolean | `false` | Create a `Subscription` for the Red Hat Data Grid Operator |
| operator.installNamespace | string | `"openshift-operators"` | The `Namespace` the Operator will be deployed in |
| operator.managedNamespaces | list | `[]` | When `operator.singleInstance` is marked as false, this instance of the  Operator will manage these namespaces |
| operator.singleInstance | boolean | `true` | Use a single operator instance to manage all Red Hat Data Grid  instances |
| operator.startingCSV | string | `nil` | The minimum `ClusterServiceVersion` for the operator |
| operator.updateApproval | string | `"Manual"` | Set the `Subscription` update approval mode. `Manual` will require install plans to be approved before upgrades will take place (recommended  for Production installations) while `Automatic` will be applied as and when they become available |
| probes | object | See child keys | Control probe override configurations for Red Hat Data Grid. If no overrides are specified sensible operator defaults will be used. |
| probes.livenessProbe | object | See child keys | Liveness probe overrides. Determines if a container is running and healthy. If a liveness probe fails, Kubernetes restarts the container to attempt recovery. |
| probes.livenessProbe.failureThreshold | int | `5` | Minimum consecutive failures for the probe to be considered failed after having succeeded.  |
| probes.livenessProbe.initialDelaySeconds | int | `nil` | Number of seconds after the container has started before liveness probes are initiated. |
| probes.livenessProbe.periodSeconds | int | `10` | How often (in seconds) to perform the probe. |
| probes.livenessProbe.successThreshold | int | `1` | Minimum consecutive successes for the probe to be considered successful after having failed. |
| probes.livenessProbe.timeoutSeconds | int | `1` | Number of seconds after which the probe times out. |
| probes.readinessProbe | object | See child keys | Readiness probe overrides. Determines if a container is ready to accept traffic. If a readiness probe fails, Kubernetes removes the pod from all matching service endpoints, preventing traffic from being routed to it until it becomes ready again. |
| probes.readinessProbe.failureThreshold | int | `5` | Minimum consecutive failures for the probe to be considered failed after having succeeded.  |
| probes.readinessProbe.initialDelaySeconds | int | `nil` | Number of seconds after the container has started before liveness probes are initiated. |
| probes.readinessProbe.periodSeconds | int | `10` | How often (in seconds) to perform the probe. |
| probes.readinessProbe.successThreshold | int | `1` | Minimum consecutive successes for the probe to be considered successful after having failed. |
| probes.readinessProbe.timeoutSeconds | int | `1` | Number of seconds after which the probe times out. |
| probes.startupProbe | object | See child keys | Startup probe overrides. Verifies whether the application within a container has successfully started. This is particularly useful for  slow-starting applications, preventing them from being prematurely killed by liveness probes before they've had a chance to fully initialize. |
| probes.startupProbe.failureThreshold | int | `600` | Minimum consecutive failures for the probe to be considered failed after having succeeded.  |
| probes.startupProbe.initialDelaySeconds | int | `3` | Number of seconds after the container has started before liveness probes are initiated. |
| probes.startupProbe.periodSeconds | int | `1` | How often (in seconds) to perform the probe. |
| probes.startupProbe.successThreshold | int | `1` | Minimum consecutive successes for the probe to be considered successful after having failed. |
| probes.startupProbe.timeoutSeconds | int | `1` | Number of seconds after which the probe times out. |
| resources | object | See child keys | Control resource configurations for Red Hat Data Grid |
| resources.limits | object | See child keys | A limit sets the maximum amount of a resource (CPU or memory) that a container is allowed to consume. |
| resources.limits.cpu | string | `"2000m"` | The maximum amount of CPU the application is allowed to use. |
| resources.limits.memory | string | `"2Gi"` | The maximum amount of memory the application is allowed to use. |
| resources.requests | object | See child keys | A request specifies the minimum amount of a resource (CPU or memory) that Kubernetes guarantees for a container. |
| resources.requests.cpu | string | `"1000m"` | The amount of CPU guaranteed for the application to use. |
| resources.requests.memory | string | `"1Gi"` | The amount of memory guaranteed for the application to use. |
| storage | object | See child keys | Control storage resources for Red Hat Data Grid. This will provide storage for preserving cluster state during shutdown and for passivated cache entries. |
| storage.ephemeral | bool | `false` | Defines whether storage is ephemeral or permanent. |
| storage.size | string | `"1Gi"` | Specifies the amount of storage for Data Grid service pods. |
| storage.storageClassName | string | `nil` | Specifies the name of a StorageClass object to use for the persistent volume claim (PVC). If left blank the persistent volume claim uses the default storage class. |

----------------------------------------------
Autogenerated from chart metadata using [helm-docs v1.14.2](https://github.com/norwoodj/helm-docs/releases/v1.14.2)
