Followed by  [Run Kubernetes clusters for less](https://aws.amazon.com/getting-started/hands-on/amazon-eks-with-spot-instances/?trk=gs_card)

## Create Cluster
```
eksctl create cluster --version=1.19 --name=eks-2nodes --nodes=2 --region=ap-southeast-1 --node-type t3.micro --node-labels="lifecycle=OnDemand" --asg-access
```


## About NGINX Ingress
[Link](https://kubernetes.github.io/ingress-nginx/deploy/)

## apply service
```
kubectl apply -f ./musician-app/service.yaml
```

## Ingress nginx
```
kubectl apply -f ingress.yaml

- check
kubectl get services -n ingress-nginx
```

```
kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/controller-v0.46.0/deploy/static/provider/aws/deploy.yaml
```
```
namespace/ingress-nginx created
serviceaccount/ingress-nginx created
configmap/ingress-nginx-controller created
clusterrole.rbac.authorization.k8s.io/ingress-nginx created
clusterrolebinding.rbac.authorization.k8s.io/ingress-nginx created
role.rbac.authorization.k8s.io/ingress-nginx created
rolebinding.rbac.authorization.k8s.io/ingress-nginx created
service/ingress-nginx-controller-admission created
service/ingress-nginx-controller created
deployment.apps/ingress-nginx-controller created
validatingwebhookconfiguration.admissionregistration.k8s.io/ingress-nginx-admission created
serviceaccount/ingress-nginx-admission created
clusterrole.rbac.authorization.k8s.io/ingress-nginx-admission created
clusterrolebinding.rbac.authorization.k8s.io/ingress-nginx-admission created
role.rbac.authorization.k8s.io/ingress-nginx-admission created
rolebinding.rbac.authorization.k8s.io/ingress-nginx-admission created
job.batch/ingress-nginx-admission-create created
job.batch/ingress-nginx-admission-patch created
```

## Cert-Manager
```
kubectl apply --validate=false -f \
https://github.com/jetstack/cert-manager/releases/download/v1.0.1/cert-manager.crds.yaml
```
## Cleanup
```
 eksctl delete nodegroup spot-node-group-2vcpu-8gb --cluster eks-ingress
 eksctl delete nodegroup spot-node-group-4vcpu-16gb --cluster eks-ingress
```




### Reference
https://www.magalix.com/blog/deploying-an-application-on-kubernetes-from-a-to-z