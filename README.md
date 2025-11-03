# datagrid-config

![Version: 0.0.1](https://img.shields.io/badge/Version-0.0.1-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square) ![AppVersion: 8.5.12](https://img.shields.io/badge/AppVersion-8.5.12-informational?style=flat-square)

A Helm chart for configuring Red Hat Data Grid Instances using the Red Hat Data Grid Operator

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| authentication | object | See child keys | Control authentication configurations for Red Hat Data Grid |
| authentication.clientCertificateAuthentication.clientCertSecretName | string | `nil` | Name of the secret that stores client certificates and the CA certificate to trust. |
| authentication.clientCertificateAuthentication.enabled | bool | `false` | Enable Client Certificate Authentication |
| authentication.clientCertificateAuthentication.strategy | string | `"Validate"` | Either `Validate`, which only checks for a valid part of the certificate chain (typically the CA) and requires credentials to be used, or `Authenticate`, which requires the client certificate to have the principal name as the `DN` of the certificate. |
| authentication.credentialsSecretName | string | `nil` | Name of the `Secret` containing an identities declaration used to configure a properties realm |
| authentication.disable | bool | `false` | Disable authentication. Not recommended for production. |
| authentication.ldapRealm | object | See child keys | Control LDAP Security Realm Configuration. This will result in a custom configuration being created as a `ConfigMap` |
| authentication.ldapRealm.connectionPooling | bool | `true` | Enables connection pooling |
| authentication.ldapRealm.connectionTimeout | string | `nil` | Sets the timeout, in milliseconds, for LDAP server connections. The default value is 5 seconds. You can optionally set one of the following units: ms (milliseconds), s (seconds), m (minutes), h (hours), d (days) |
| authentication.ldapRealm.credentialAlias | string | `nil` | Name of the key from the `credentialsStore.secretName` that contains the password used to connect to the LDAP server |
| authentication.ldapRealm.directVerification | bool | `false` | Configures the realm to verify credentials by connecting to LDAP servers with the account |
| authentication.ldapRealm.enabled | bool | `false` | Enable LDAP security realm |
| authentication.ldapRealm.identityMapping | object | See child keys | Specifies configuration options that define how principals are mapped to corresponding entries in LDAP servers |
| authentication.ldapRealm.identityMapping.attributeMapping | list | See child keys | Specifies the attribute mappings defined for this resource |
| authentication.ldapRealm.identityMapping.filterName | string | `nil` | Specifies the LDAP filter that retrieves an identity by name. In the default value, "{0}" is replaced with the searched identity name and "rdn_identifier" is replaced with the value of the "rdn-identifier" attribute. |
| authentication.ldapRealm.identityMapping.rdnIdentifier | string | `nil` | Specifies an LDAP attribute that contains the user name and appears in the path of new entries |
| authentication.ldapRealm.identityMapping.searchDn | string | `nil` | Names the context for query execution |
| authentication.ldapRealm.identityMapping.searchRecursive | bool | `false` | Performs recursive queries |
| authentication.ldapRealm.identityMapping.userPasswordMapper | object | See child keys | Specifies the user password credential mapping defined for this resource |
| authentication.ldapRealm.identityMapping.userPasswordMapper.enabled | bool | `false` | Enables the user password credential mapper. This will be enabled automatically if `authentication.ldapRealm.directVerification` is set to `true` |
| authentication.ldapRealm.identityMapping.userPasswordMapper.from | string | `"userPassword"` | The name of the LDAP attribute to map to an identity user password credential. |
| authentication.ldapRealm.identityMapping.userPasswordMapper.verifiable | bool | `false` | If the password credential is verifiable |
| authentication.ldapRealm.isActiveDirectory | bool | `false` | If set `directVerification` will be set to true automatically and endpoints will be configured to allow `BASIC` authentication on the `restConnector` endpoint and `PLAIN` authentication on the `hotrodConnector` endpoint |
| authentication.ldapRealm.nameRewriter | object | See child keys | Specifies a name rewriter that transforms names returned by a realm. Only one can be active at a time. |
| authentication.ldapRealm.nameRewriter.casePrincipalTransformer | object | See child keys | Specifies a PrincipalTransformer definition using case conversion |
| authentication.ldapRealm.nameRewriter.casePrincipalTransformer.enabled | bool | `false` | Enables the `CasePrincipalTransformer` |
| authentication.ldapRealm.nameRewriter.casePrincipalTransformer.uppercase | bool | `true` | Whether to transform to UPPERCASE or lowercase |
| authentication.ldapRealm.nameRewriter.commonNamePrincipalTransformer | object | See child keys | Specifies a PrincipalTransformer definition which extracts the first CommonName (CN) from a DistinguishedName (DN) |
| authentication.ldapRealm.nameRewriter.commonNamePrincipalTransformer.enabled | bool | `false` | Enables the `CommonNamePrincipalTransformer` |
| authentication.ldapRealm.nameRewriter.regexPrincipalTransformer | object | See child keys | Specifies a PrincipalTransformer definition using regular expressions and Matcher based replacement |
| authentication.ldapRealm.nameRewriter.regexPrincipalTransformer.enabled | bool | `false` | Enables the `RegexPrincipalTransformer` |
| authentication.ldapRealm.nameRewriter.regexPrincipalTransformer.pattern | string | `nil` | Specifies the regular expression for this PrincipalTransformer |
| authentication.ldapRealm.nameRewriter.regexPrincipalTransformer.replacement | string | `nil` | Specifies the replacement string for the PrincipalTransformer |
| authentication.ldapRealm.pageSize | int | `nil` | Sets the page size for realm iteration. The default value is 50 |
| authentication.ldapRealm.principal | string | `nil` | Specifies the user principal for LDAP server connections |
| authentication.ldapRealm.readTimeout | string | `nil` | Sets the read timeout, in milliseconds, for LDAP server operations. The default value is 1 minute. You can optionally set one of the following units: ms (milliseconds), s (seconds), m (minutes), h (hours), d (days) |
| authentication.ldapRealm.referralMode | string | `nil` | Specifies if LDAP server referrals are followed and corresponds to the REFERRAL ("java.naming.referral") environment property. Values are "ignore", "follow" (default), and "throw" |
| authentication.ldapRealm.url | string | `nil` | Specifies the URL for LDAP server connections in the format ldap[s]://{hostname}:{port} |
| authentication.propertiesRealm | object | See child keys | Control Properties Security Realm Configuration when using multiple security realms |
| authentication.propertiesRealm.enabled | bool | `true` | Enable properties security realm |
| authorization | object | See child keys | Control authorization for Red Hat Data Grid. |
| authorization.customRoles | object | See child keys | Custom RBAC roles permission configuration. |
| authorization.customRoles.enabled | bool | `false` | Enable custom role configuration. |
| authorization.customRoles.roles | list | See example role entry | List of custom role configurations. |
| authorization.customRoles.roles[0].name | string | `"custom-admin"` | Name of the custom role |
| authorization.customRoles.roles[0].permissions | list | `["ALL"]` | A list of permissions with possible values being `ALL` `ALL_READ`, `ALL_WRITE`, `LISTEN`, `EXEC`, `MONITOR`, `CREATE` |
| authorization.enabled | bool | `false` | Enable authorization to provide more granular security control over the Red Hat Data Grid cluster. |
| autoscaling | object | See child keys | Control autoscaling for Red Hat Data Grid. This should be disabled during upgrade procedures as it will interfere with the upgrade process. |
| autoscaling.cpuAverageUtilization | int | `nil` | CPU percentage utilization that triggers a scaling operation. |
| autoscaling.enabled | bool | `false` | Enable autoscaling. |
| autoscaling.maxReplicas | int | `3` | Maximum amount of pods. |
| autoscaling.memoryAverageUtilization | int | `nil` | Memory percentage utilization that triggers a scaling operation. |
| autoscaling.minReplicas | int | `1` | Minimum amount of pods. |
| availability | object | See child keys | Control high availability for Red Hat Data Grid. |
| availability.antiAffinitityType | string | `"preferred"` | One of `preferred`, for `preferredDuringSchedulingIgnoredDuringExecution`, or `required`, for `requiredDuringSchedulingIgnoredDuringExecution`, modes. |
| availability.enabled | bool | `true` | Enable high availability using anti-affinity. |
| availability.hostname | bool | `true` | Use `kubernetes.io/hostname` `topologyKey` |
| availability.zone | bool | `false` | Use `topology.kubernetes.io/zone` `topologyKey` |
| caches | string | See child keys | Cache configuration for caches |
| credentialsStore | object | See child keys | Configuration of a `Secret` used to store sensitive information |
| credentialsStore.enabled | boolean | `false` | Use a `Secret` to store sensitive information such as credentials |
| credentialsStore.secretName | string | `nil` | The name of the `Secret` used to store sensitive information |
| customConfig | object | See child keys | Settings related to the Red Hat Data Grid Operator Cluster |
| customConfig.config | object | `nil` | The custom Red Hat Data Grid configuration |
| customConfig.enabled | boolean | `false` | Create a `ConfigMap` with a custom Red Hat Data Grid configuration |
| encryption | object | See child keys | Control encryption configurations for Red Hat Data Grid |
| encryption.certSecretName | string | `nil` | Name of the secret containing the custom TLS/SSL certificate and key |
| encryption.disable | bool | `false` | Disable encryption. Not recommended for production. |
| endpoints | object | See child keys | Control endpoints when multiple security realms are defined. This will have no effect unless the `authentication.ldapRealm.enabled` value is set to `true` |
| endpoints.memcachedConnector | bool | `false` | Enable the Memcached Endpoint |
| endpoints.respConnector | bool | `false` | Enable the Redis Endpoint |
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
