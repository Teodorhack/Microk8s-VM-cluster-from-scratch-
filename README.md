
```markdown
# ☸️ High-Availability Kubernetes Home Lab with MicroK8s

How to use this guide?

Read the part_1,2,3 txt files that you can find in the step-2 branch and they will lead you.
Keep in mind that this guidE was done so I can better understand this project and to share with you the experience of building a microk8s cluster. ENJOY

Welcome to my **Home Lab** project! In this setup, I built a **High-Availability (HA) Kubernetes cluster** using **[MicroK8s](https://microk8s.io)** on **Ubuntu Server 24.04 LTS**. This lab is ideal for experimenting with Kubernetes in a small-scale environment. Here's a quick overview of what you'll find:

## 🔧 Key Features:
- **High Availability**: The cluster is resilient, meaning if one node goes down, the others keep running. We use a minimum of 3 nodes for this.
- **Node Setup**: Added multiple nodes to the cluster for redundancy and load balancing.
- **Networking with Ingress**: Services are exposed externally using **MetalLB** and **Nginx Ingress**.
  
## 🚀 Installation Steps:
1. **Install MicroK8s** on each Ubuntu server:
    ```bash
    sudo snap install microk8s --classic
    ```
2. **Disable Swap** and join nodes to the cluster to enable HA automatically:
    ```bash
    sudo sed -i '/ swap / s/^/#/' /etc/fstab
    microk8s add-node
    ```

## ⚙️ Addons and Services:
- **Enable HA and essential addons**:
    ```bash
    microk8s enable ha-cluster dns ingress metallb
    ```
- **Deploy a demo app** using HTTPD to test the cluster and Ingress:
    ```bash
    microk8s kubectl create deployment demo --image=httpd
    microk8s kubectl expose deployment demo --port=80
    ```

## 🌐 Accessing the Cluster:
To expose services outside the cluster, we configure **MetalLB** with a range of IPs and use **Ingress** for routing traffic. 

Stay tuned for more updates as I continue improving and experimenting with this home lab! 🎉
```

This README captures the essential steps and features of your high-availability Kubernetes cluster, based on the guide you're following. You can adjust and expand it based on additional components you might add later!
