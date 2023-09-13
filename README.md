# kfp-hello-world

## Installation instructions

Assumes pyenv and poetry. 

```bash
pyenv install 3.10.0
pyenv local 3.10.0
poetry new kfp-hello-world
cd kfp-hello-world
poetry config virtualenvs.in-project true # facilitates VS Code finding poetry venv
poetry env use 3.10.0
poetry add kfp=2.0.1
# When you come back to this later, may need to activate poetry shell
# poetry shell
code .
```

In VS Code, open Command Palette, Select Python Interpreter... select matching
poetry env.

Run code by right-clicking and running in IDE or use 
`poetry run python <script>.py` from shell.

### Kubeflow Pipelines

Assumes KIND.

```bash
kind create cluster --name mykfp
export PIPELINE_VERSION=2.0.1
kubectl apply -k "github.com/kubeflow/pipelines/manifests/kustomize/cluster-scoped-resources?ref=$PIPELINE_VERSION"
kubectl wait --for condition=established --timeout=60s crd/applications.app.k8s.io
kubectl apply -k "github.com/kubeflow/pipelines/manifests/kustomize/env/dev?ref=$PIPELINE_VERSION"
```

Forward port for KFP UI:

```bash
kubectl port-forward -n kubeflow svc/ml-pipeline-ui 8080:80
```
