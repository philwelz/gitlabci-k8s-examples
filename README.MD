# GitLabCI Kubernetes examples

Examples for deploying Helm Charts and Kubernetes manifests via GitLabCI.
 
- [Example for deyploying Helm Charts with GitLabCI](https://github.com/philwelz/gitlabci-k8s-examples/blob/master/helm.pipeline.yaml)
- [Example for deyploying Kubernetes manifests with GitLabCI](https://github.com/philwelz/gitlabci-k8s-examples/blob/master/k8s.pipeline.yaml)

## GitLab CI/CD Variables Configuration

:exclamation: Please define `P_KUBE_NAMESPACE`, `P_CONTAINER_TEST_IMAGE` & `P_IMAGE_REGISTRY` on project level manually :exclamation:

Each variable is applied to the environment defined above

| Variable                         | Scope    | Value                   | What it is  |
| --------                         | -------- | --------                | ------------|
| `KUBE_URL`                       | Global   | `https://API:6443`      | Equal to the API URL.  |
| `CI_REGISTRY`                    | Global   | `registry.example.com"` | Equal to GitLan Image registry|
| `G_DOCKER_IMAGE`                 | Group    | `docker:19.03.12`       | Global defined Docker Image and Version |
| `G_GITLAB_ADMIN`                 | Group    | `gitlab-admin`          | GitLab Service Account for Kubernetes  |
| `G_GITLAB_ADMIN_DEV_TOKEN`       | Group    | `TOKEN`                 | Token for Gitlab Service Account in Dev Environment |
| `G_GITLAB_ADMIN_PROD_TOKEN`      | Group    | `TOKEN`                 | Token for Gitlab Service Account in Prod Environment |
| `G_GITLAB_API_TOKEN`             | Group    | `TOKEN`                 | Token for accessing the API  |
| `G_REGISTRY_EMAIL`               | Group    | `EMAIL`                 | Simply an Email address |
| `G_REGISTRY_TOKEN`               | Group    | `TOKEN`                 | Token for the Development Group Registrsy |
| `G_REGISTRY_USER`                | Group    | `USER`                  | User to access the Registry from the Development Group |
| `G_SECRET_NAME`                  | Group    | `gitlab-readonly`       | Name of the Secret in Kubernetes |
| `G_KUBE_MAJOR_VERSION`           | Group    | `1.18.0`                | Global defined Kubernetes Version |
| `G_KUBE_PROD_CLUSTER`            | Group    | `kubernetes-prod`       | Kubernetes Cluster Name |
| `G_KUBE_PROD_CLUSTER_CA`         | Group    | `CA  File`              | CA File for Cluster access |
| `G_KUBE_DEV_CLUSTER`             | Group    | `kubernetes-dev`        | Kubernetes Dev Cluster Name |
| `G_KUBE_DEV_CLUSTER_CA`          | Group    | `CA File`               | CA File for Dev Cluster access |
| `KUBE_DEV_URL`                   | Group    | `https://PROD_API:6443` | Equal to the K8s Dev Environment API URL  |
| `KUBE_PROD_URL`                  | Group    | `https://DEV_API:6443`  | Equal to the K8s Prod Environment API URL  |
| `P_KUBE_NAMESPACE`               | Project  | `NAMESPACE`             | Target Kubernetes Namespace |
| `P_CONTAINER_TEST_IMAGE`         | Project  | `IMAGE`                 | Name of the Image user for Vuln Scans without Tag |
| `P_IMAGE_REGISTRY`               | Project  | `IMAGE_REGISTRY`        | Specific URL to target Project Registry |
| `UPSTREAM_SemVer`                | CI/CD    | `auto via CI/CD`        | VAR for versioning Apps from Upstream pipelines |
| `GitVersion_SemVer`              | CI/CD    | `auto via CI/CD`        | VAR for versioning Helm Charts |

## Directory Layout

### Helm

```bash
Repository
│   .pipeline.yaml
│   README.md
│   ...
│ 
└───chart
    │   Chart.yaml
    │   values.yaml
    │
    └───templates
    │     deplyoment.yaml
    │     ingress.yaml
    │     ...
    │ 
    └───dev
    │     values.yaml
    │    
    └───prod
          values.yaml
```

### Kubernetes manifests

```bash
Repository
│   .pipeline.yaml
│   README.md
│   ...
│ 
└───k8s
      deplyoment.yaml
      ingress.yaml
      ...
```