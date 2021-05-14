Followed by  [Run Kubernetes clusters for less](https://aws.amazon.com/getting-started/hands-on/amazon-eks-with-spot-instances/?trk=gs_card)

# Create Cluster
```
eksctl create cluster --version=1.19 --name=eks-3nodes --nodes=3 --region=ap-southeast-1 --node-type t3.micro --node-labels="lifecycle=OnDemand" --asg-access
```



# Cleanup
```
 eksctl delete nodegroup spot-node-group-2vcpu-8gb --cluster eks-3nodes
 eksctl delete nodegroup spot-node-group-4vcpu-16gb --cluster eks-3nodes
```
