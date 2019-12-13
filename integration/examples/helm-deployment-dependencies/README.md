### Example: deploy helm charts with local dependencies

This example follows the [helm](../helm-deployment) example, but with a local chart as a dependency.

The `skipBuildDependencies` option is used to skip the `helm dep build` command. This must be disabled for charts with local dependencies.

The image can be passed to the subchart using the standard Helm format of `subchart-name.value`.

```yaml
deploy:
  helm:
    releases:
    - name: skaffold-helm
      chartPath: skaffold-helm
      namespace: skaffold
      skipBuildDependencies: true # Skip helm dep build
      values:
        image: skaffold-helm
        "subchart.image": gcr.io/k8s-skaffold/skaffold-helm # Set image for subchart
      valuesFiles:
        - helm-values-file.yaml
```

<a href="vscode://googlecloudtools.cloudcode/shell?repo=https://github.com/GoogleContainerTools/skaffold.git&subpath=/examples/helm-deployment-dependencies"><img width="286" height="50" src="/docs/static/images/open-cloud-code.png"></a>