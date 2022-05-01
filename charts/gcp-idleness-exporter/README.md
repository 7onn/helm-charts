# gcp-idleness-exporter

![Version: 0.8.1](https://img.shields.io/badge/Version-0.8.1-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square) ![AppVersion: v1.1.1](https://img.shields.io/badge/AppVersion-v1.1.1-informational?style=flat-square)

A Helm chart for running gcp-idleness-exporter on Kubernetes

## Maintainers

| Name | Email | Url |
| ---- | ------ | --- |
| 7onn | devbytom@gmail.com |  |

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| affinity | object | `{}` |  |
| credentials | object | `{"existingSecret":"","name":"","secretContents":{"service-account-keyfile.json":"{\n  \"type\": \"service_account\",\n  \"project_id\": \"\",\n  \"private_key_id\": \"\",\n  \"private_key\": \"-----BEGIN PRIVATE KEY-----\\n-----END PRIVATE KEY-----\\n\",\n  \"client_email\": \"\",\n  \"client_id\": \"\",\n  \"auth_uri\": \"\",\n  \"token_uri\": \"\",\n  \"auth_provider_x509_cert_url\": \"\",\n  \"client_x509_cert_url\": \"\"\n}\n"},"useSecret":true}` | Info about the secret bearing the GCP service-account-keyfile.json |
| credentials.existingSecret | string | `""` | Name of a pre-existing secret containing service-account-keyfile.json |
| credentials.name | string | `""` | Name of the secret to create if `useSecret` is true and `existingSecret` is empty |
| credentials.secretContents | object | `{"service-account-keyfile.json":"{\n  \"type\": \"service_account\",\n  \"project_id\": \"\",\n  \"private_key_id\": \"\",\n  \"private_key\": \"-----BEGIN PRIVATE KEY-----\\n-----END PRIVATE KEY-----\\n\",\n  \"client_email\": \"\",\n  \"client_id\": \"\",\n  \"auth_uri\": \"\",\n  \"token_uri\": \"\",\n  \"auth_provider_x509_cert_url\": \"\",\n  \"client_x509_cert_url\": \"\"\n}\n"}` | Content of service-account-keyfile.json to create if `useSecret` is true and `existingSecret` is empty |
| credentials.useSecret | bool | `true` | Whether a secret should be used. Set to false if using workload identity instead of providing the key file. |
| customLabels | object | `{}` | Custom labels to apply on every resource managed by this Chart |
| env | list | `[{"name":"GCP_PROJECT_ID","value":""},{"name":"GCP_REGIONS","value":""}]` | Workload's environment variables |
| env[0] | object | `{"name":"GCP_PROJECT_ID","value":""}` | GCP Project ID to monitor |
| env[1] | object | `{"name":"GCP_REGIONS","value":""}` | Comma-separated regions to monitor (e.g: us-central1,us-east1,southamerica-east1) |
| fullnameOverride | string | `""` |  |
| image | object | `{"pullPolicy":"IfNotPresent","repository":"devbytom/gcp-idleness-exporter","tag":""}` | Container image |
| imagePullSecrets | list | `[]` |  |
| kubeVersionOverride | string | `""` |  |
| nameOverride | string | `""` |  |
| nodeSelector | object | `{}` |  |
| podAnnotations | object | `{}` |  |
| podDisruptionBudget | object | `{"annotations":{},"create":false,"minAvailable":1}` | Whether to create a PodDisruptionBudget resource |
| podSecurityContext | object | `{}` |  |
| replicaCount | int | `1` |  |
| resources.limits.cpu | string | `"100m"` |  |
| resources.limits.memory | string | `"256Mi"` |  |
| resources.requests.cpu | string | `"100m"` |  |
| resources.requests.memory | string | `"128Mi"` |  |
| securityContext | object | `{}` |  |
| service.port | int | `80` |  |
| service.targetPort | int | `5000` |  |
| service.type | string | `"ClusterIP"` |  |
| serviceAccount.annotations | object | `{}` | Annotations to add to the service account |
| serviceAccount.create | bool | `true` | Specifies whether a service account should be created |
| serviceAccount.name | string | `""` | The name of the service account to use. If not set and create is true, a name is generated using the fullname template |
| serviceMonitor | object | `{"create":false,"scrapeInterval":"5m","scrapeTimeout":"30s"}` | Whether to create a Prometheus operator ServiceMonitor resource |
| tolerations | list | `[]` |  |

----------------------------------------------
Autogenerated from chart metadata using [helm-docs v1.7.0](https://github.com/norwoodj/helm-docs/releases/v1.7.0)