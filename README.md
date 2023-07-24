# Test Application for Serverless Examples
This is a test Go application for serverless examples.

## Pre-requisites:
- Go is installed. Find the installation instructions [here](https://go.dev/doc/install).
- AWS CLI is installed and configured. Find the installation instructions [here](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html).
- GoReleaser is installed. Find the installation instructions [here](https://goreleaser.com/install/)

### Apply ArgoCD application
The applications contains the claim and the deployment.
```
kubectl apply -f argocd-app.yaml
```

### Navigate to the ArgoCD UI
Find the ArgoCD URL:
```
kubectl -n argocd get svc argo-cd-argocd-server -o jsonpath='{.status.loadBalancer.ingress[0].hostname}'
```
The username is `admin` and the password can be obtained by executing:
```
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d
```

### Sync the ArgoCD app and watch the lambda-processor app come up.
![Lambda Processor App ArgoCD](argo.gif)
