# desafio

# Tecnologias Utilziadas:
EKS, terraform, grafana, prometheus, helm chart

# Acesso ao grafana:
https://grafana-lab.amldev.com.br/login
user: user1
pass: user1

# Acesso ao prometheus:
https://prometheus-lab.amldev.com.br/graph

# Acesso ao jenkins:
http://34.221.245.49:8080/
user: user1
pass: user1

# Create infras as code - terraform
Create vpc, eks cluster, ec2 (jenkins)

terraform init
terraform plan
terraform apply --auto-appove

# install helm
curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3
chmod 700 get_helm.sh
./get_helm.sh

# install kubectl
https://kubernetes.io/docs/tasks/tools/install-kubectl-linux/

# install eksctl
https://eksctl.io/introduction/#installation

# helm
helm create helm-chart
change image repository to ecr repo in values.yaml
change service type to LoadBalancer in values.yaml
change container port to 8080 in deployment.yaml

# k8s 
# create namespace
kubectl create ns helm-deployment