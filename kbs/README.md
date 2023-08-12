# Kubernetes tool

## Install KBS on a Bare Metal Server


 ### Install  Ansible

Ubuntu
```
sudo apt update
sudo apt install software-properties-common
sudo apt-add-repository --yes --update ppa:ansible/ansible
sudo apt install ansible
```

Fedora
```
sudo dnf install ansible
```

MacOS with Homebrew
```
brew install ansible
```

Windows
```
pip install ansible
```

### Install KBS using Ansible

### Create an inventory file

example of inventory can be found on this [Website](https://docs.ansible.com/ansible/latest/user_guide/intro_inventory.html)

### Run the playbook

```bash
ansible-playbook -i inventory/hosts.ini kbs.yml
```


## Load Balancer

## On Azure

1) Setup Azure CLI on your machine
 
go to [Azure CLI](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli?view=azure-cli-latest) and follow the instructions

2) Login to Azure
```bash
az login
```

3) Create a resource group
```bash
az group create --name myResourceGroup --location eastus
```


```bash
kubectl apply -f LoadBalancer/load-balancer-service.yaml
```


## On Bare Metal

### Install MetalLB

```bash
kubectl apply -f https://raw.githubusercontent.com/metallb/metallb/v0.13.10/config/manifests/metallb-native.yaml
```

### Configure MetalLB

```bash
kubectl apply -f LoadBalancer/metallb-configmap.yaml
```


## Ingress Controller

### Install Nginx Ingress Controller

```bash
kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/master/deploy/static/mandatory.yaml
```

