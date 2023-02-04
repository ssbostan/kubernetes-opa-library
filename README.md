# kubernetes-opa-library

[![GitHub stars](https://img.shields.io/github/stars/ssbostan/kubernetes-opa-library)](https://github.com/ssbostan/kubernetes-opa-library/stargazers)
![LinkedIn Follow](https://shields.io/badge/style-ssbostan-black?logo=linkedin&label=LinkedIn&link=https://www.linkedin.com/in/ssbostan)
![GitHub last commit](https://img.shields.io/github/last-commit/ssbostan/kubernetes-opa-library)
[![GitHub forks](https://img.shields.io/github/forks/ssbostan/kubernetes-opa-library)](https://github.com/ssbostan/kubernetes-opa-library/network)
[![GitHub issues](https://img.shields.io/github/issues/ssbostan/kubernetes-opa-library)](https://github.com/ssbostan/kubernetes-opa-library/issues)

The complete library for Kubernetes OPA Gatekeeper policies with a quickly deployable Helm chart.

YOU LIKE IT? STAR IT. ![GitHub Repo stars](https://img.shields.io/github/stars/ssbostan/kubernetes-opa-library?style=social)

## What do we have here?

Here, we have two helm charts, the OPA Gatekeeper Templates helm chart and the OPA Gatekeeper Constraints helm chart. The Templates helm chart deploys OPA templates, Rego language codes, and the Constraints helm chart creates objects from deployed templates. You can enable/disable or change constraints config from its values file.

## Why do we need two separate the Helm charts?

It's because of the nature of Helm mixed with OPA Gatekeeper resources. Typically, Helm looks for all resources available in the cluster before deploying them into the cluster. In the case of new resources which depend on CRDs, it deploys CRDs first and then deploys resources, but OPA Gatekeeper Templates are not CRDs. They look like regular resources and create CRDs behind the scenes. Therefore, Helm cannot recognize them as CRDs and deploy them before Constraints into the cluster. On the other hand, Constraints need Templates CRDs to be deployed to the cluster. So, to deploy OPA Policies with Helm, we need two Helm charts. The OPA Gatekeeper Templates helm chart should be deployed first, and after creating CRDs, we have to deploy the OPA Gatekeeper Constraints helm chart.

# Get started guide:

The `templates` directory consists of OPA Gatekeeper templates helm chart, and the `constraints` directory consists of OPA Gatekeeper constraints helm chart. To test policies before/after deployment, you can use all resources in the `tests` directory, which consists of many Kubernetes resources.

```bash
# To Install:
./install

# To Upgrade:
./upgrade

# To Uninstall:
./uninstall
```

You can also run Helm commands directly or override constraints `values.yaml` file.

# License:

Apache License 2.0, see [LICENSE](./LICENSE).

Copyright &copy; 2022-2023 Saeid Bostandoust <ssbostan@yahoo.com>
