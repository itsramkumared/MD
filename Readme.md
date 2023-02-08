***Create Cluster***

```eksctl create cluster --name=eks-planet9 --region=us-east-1 --zones=us-east-1a,us-east-1b --without-nodegroup```

***Get List of clusters***

```eksctl get cluster```                  

***Template***
```eksctl utils associate-iam-oidc-provider \
    --region region-code \
    --cluster <cluter-name> \
    --approve```

***Replace with region & cluster name***

```eksctl utils associate-iam-oidc-provider --region us-east-1 --cluster eks-planet9 --approve```

***Create Public Node Group***   
```eksctl create nodegroup --cluster=eks-planet9 \
                       --region=us-east-1 \
                       --name=eks-planet9-ng-public1 \
                       --node-type=t2.medium \
                       --nodes=2 \
                       --nodes-min=2 \
                       --nodes-max=4 \
                       --node-volume-size=20 \
                       --ssh-access \
                       --ssh-public-key=p9-ec2 \
                       --managed \
                       --asg-access \
                       --external-dns-access \
                       --full-ecr-access \
                       --appmesh-access \
                       --alb-ingress-access ```

eksctl create nodegroup --cluster=eks-planet9 --region=us-east-1 --name=eks-planet9-ng-private1 --node-type=t2.medium --nodes=2 --nodes-min=2 --nodes-max=4 --node-volume-size=20 --ssh-access --ssh-public-key=p9-ec2 --managed --asg-access --external-dns-access --full-ecr-access --appmesh-access --alb-ingress-access --node-private-networking
eksctl create nodegroup --cluster=eks-planet9 --region=us-east-1 --name=eks-planet9-ng-public1 --node-type=t2.medium --nodes=2 --nodes-min=2 --nodes-max=4 --node-volume-size=20 --ssh-access --ssh-public-key=p9-ec2 --managed --asg-access --external-dns-access --full-ecr-access --appmesh-access --alb-ingress-access


***List EKS clusters***

eksctl get cluster

**List NodeGroups in a cluster***

eksctl get nodegroup --cluster=eks-planet9

***List Nodes in current kubernetes cluster***

kubectl get nodes -o wide

***Our kubectl context should be automatically changed to new cluster***

kubectl config view --minify

***List EKS Clusters***

eksctl get clusters

***Capture Node Group name***

eksctl get nodegroup --cluster=<clusterName>
eksctl get nodegroup --cluster=eks-planet9

***Delete Node Group***

eksctl delete nodegroup --cluster=<clusterName> --name=<nodegroupName>
eksctl delete nodegroup --cluster=eks-planet9 --name=eks-planet9-ng-public1

***Delete Cluster***

eksctl delete cluster <clusterName>
eksctl delete cluster eks-planet9

aws eks --region us-east-1 update-kubeconfig --name eks-planet9

-[For Deployments](https://github.com/itsramkumared/planet9-kubernetes-deployments)