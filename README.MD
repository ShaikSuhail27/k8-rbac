##### RBAC ################

* RBAC-->role based access control
* IAM is used for authentication purpose
* K8-RBAC is used for authorization purpose
steps:
1. Need to create one IAM user for authentication purpose.
2. namespace
3. role (what are the permissions we need to give)
4. rolebinding (for which user we need to bind) 
5. There will be default config map aws-auth in kubesystem namespace and here we need to map IAM user and k8-rbac
    kubectl get configmap aws-auth -n kube-system -o yaml
6.  eksctl create iamidentitymapping --cluster eks-spot-cluster --region=us-east-1 \
    --arn arn:aws:iam::212837455940:user/suhail --username suhail --group Roboshop-Admin \
    --no-duplicate-arns
7. we need to cinfigure the cluster role and cluster role binding