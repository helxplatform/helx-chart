# resty

![Version: 1.0.5](https://img.shields.io/badge/Version-1.0.5-informational?style=flat-square) ![AppVersion: 2.0.1](https://img.shields.io/badge/AppVersion-2.0.1-informational?style=flat-square)

A Helm chart for Kubernetes

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| DEV_PHASE.dev | bool | `false` | Set the DEV_PHASE.dev True, if Appstore/Tycho running locally. Else, set it to False |
| airflow.authenticate | bool | `true` |  |
| artifactCache | object | `{"authenticate":false,"enabled":false,"port":8080,"serviceName":"artifact-cache"}` | Optional /artifact route to an in-cluster artifact-cache service (replaces the ambassador Mapping for /artifact). Enable in envs that serve the helx-apps registry/specs from an artifact cache (e.g. air-gapped OpenShift). Off by default. Set authenticate=true to require the auth_request gate on /artifact. |
| basicAuth | object | `{"enabled":false,"password":"defaultPassword","username":"defaultUser"}` | Creates a basicAuth scheme preventing un-authenticated access to the whole site. |
| basicAuth.password | string | `"defaultPassword"` | Password, make sure to override. |
| basicAuth.username | string | `"defaultUser"` | Username , make sure to override. |
| dnsResolver | string | `"kube-dns.kube-system.svc.cluster.local"` | PROTOTYPE (ambassador removal): cluster DNS used to re-resolve the dynamic /private/ upstreams at request time. Must point at your cluster DNS (CoreDNS/kube-dns). Some nginx builds require an IP here rather than a name -- set the CoreDNS service ClusterIP if the hostname form fails. |
| external_http_host | bool | `false` | If using an external http proxy host set this to true and specify serverName.  Used for TACC. |
| fullnameOverride | string | `""` |  |
| global.airflow_service_name | string | `"airflow-webserver"` |  |
| global.ambassador_service_name | string | `"ambassador"` |  |
| global.apps_namespace | string | `""` | Namespace where Tycho launches app pods (for /private DNS names). Defaults to the release namespace when empty. |
| global.appstore_service_name | string | `nil` | PROTOTYPE (ambassador removal): direct backend service names that were previously reached only through the "ambassador" service. appstore_service_name / ui_service_name: leave null to auto-derive — the bare chart name ("appstore"/"ui") when resty is deployed on its own, or "<release>-appstore"/"<release>-ui" when deployed as a subchart of the umbrella. Set explicitly only if your Service names differ. |
| global.appstore_sockets_service_name | string | `"appstore-sockets-service"` |  |
| global.cluster_dns_suffix | string | `"svc.cluster.local"` |  |
| global.dug_search_client_service_name | string | `"dug-search-client"` |  |
| global.dug_web_service_name | string | `"dug-web"` |  |
| global.restartr_api_service_name | string | `"restartr-api-service"` |  |
| global.ui_service_name | string | `nil` |  |
| image.pullPolicy | string | `"IfNotPresent"` |  |
| image.repository | string | `"bitnami/openresty"` |  |
| image.tag | float | `1.21` | Overrides the image tag whose default is the chart appVersion. |
| imagePullSecrets | list | `[]` |  |
| ingress.admin.annotations | object | `{}` |  |
| ingress.admin.enabled | bool | `false` | Create an additional Ingress to restrict access to /admin routes |
| ingress.annotations | object | `{}` |  |
| ingress.create | bool | `false` | Create an Ingress resource or not. New installations of helx should set this to true to avoid needing to request a static IP. |
| ingress.ingressClassName | string | `nil` | Set to use a specific ingress class other than the default. |
| ingress.tls.enabled | bool | `true` | Values inserted into the TLS block come from SSL.nginxTLSSecret and service.serverName for backward compatibility |
| nameOverride | string | `""` |  |
| replicaCount | int | `1` |  |
| resources.limits.cpu | string | `"100m"` |  |
| resources.limits.memory | string | `"128Mi"` |  |
| resources.requests.cpu | string | `"50m"` |  |
| resources.requests.memory | string | `"32Mi"` |  |
| restartrApi | bool | `false` |  |
| service.IP | string | `nil` | The static IP for this service, assigned to you by cluster administrators. Ignored if ingress.create=true. |
| service.httpPort | int | `80` |  |
| service.httpTargetPort | int | `8080` |  |
| service.httpsPort | int | `443` |  |
| service.httpsTargetPort | int | `8443` |  |
| service.serverName | string | `"_"` |  |
| service.type | string | `"LoadBalancer"` | can be LoadBalancer or ClusterIP. If ingress.create=true, this setting is ignored and defaulted to ClusterIP |
| stubStatus.enabled | bool | `false` |  |
| stubStatus.localhostOnly | bool | `true` |  |
| stubStatus.stubStatusLocation | string | `"/nginx_status"` |  |
| varStorage.claimName | string | `nil` |  |
| varStorage.existingClaim | bool | `false` |  |
| varStorage.storageClass | string | `nil` |  |
| varStorage.storageSize | string | `"2Gi"` |  |
| workerConnections | int | `1024` |  |

----------------------------------------------
Autogenerated from chart metadata using [helm-docs v1.11.0](https://github.com/norwoodj/helm-docs/releases/v1.11.0)
