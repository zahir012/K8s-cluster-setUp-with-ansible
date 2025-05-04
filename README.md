##Install Kubernetes cluster Using Ansible on Ubuntu 24.04

## Introduction 

Deploying Kubernetes on Ubuntu 24.04 can be a complex task. However, using Ansible roles simplifies this process significantly. Ansible, an open-source automation tool, allows you to automate and manage configuration tasks efficiently. In a previous article, we reviewed how to manually deploy Kubernetes on Ubuntu 23.10. In this guide, we will walk through the steps to deploy a Kubernetes cluster on Ubuntu 24.04 using Ansible roles

## Prerequisites

Before we begin, ensure you have the following:

1. A stable internet connection
2. A control node with Ansible installed (preferably Ubuntu 24.04).
3. At least two Ubuntu 24.04 nodes (one master and one worker).
4. SSH access to all nodes from the control node.
5. Establish a user account with sudo (root) privileges on all nodes
6. Basic knowledge of Ansible and Kubernetes.


## Install Kubernetes Using Ansible on Ubuntu 24.04

Let’s proceed with the installation. First things first, update all nodes with the following command (below). Please read each instruction carefully before executing:

=>> sudo apt update -y && sudo apt upgrade -y

=>> sudo adduser sysadmin  | create operational user 

=>> sudo usermod -aG sudo sysadmin 

First, update your package lists and install Ansible on your control node only:

=>> sudo apt install ansible -y

=>> ssh-keygen -t rsa -b 4096 -C "your_email@example.com"

=>> ssh-copy-id your_privileged_user@your_master_node_ip_address

=>> ssh-copy-id your_privileged_user@your_worker_node_ip_address

## Define Your Inventory File and create Ansible Role as per project structure

=>> ansible-galaxy init kubernetes_master

=>> ansible-galaxy init kubernetes_worker

=>> ansible-galaxy init kubernetes_network


## Now that we have reviewed each Ansible role necessary for configuring a Kubernetes cluster, we will proceed with executing the playbook as per below command

=>> ansible-playbook -i hosts cluster-setup.yml

## Use Kubectl Commands

=>> kubectl get nodes

=>> kubectl get pods --all-namespaces

=>> kubectl get services
