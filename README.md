# kuberinst

K8S Test Lab

Install docker &amp; k8s on Ubuntu 18.04 (perhaps, Debian 10)

- network:
https://github.com/coreos/flannel/blob/master/Documentation/kube-flannel.yml (used bu default)
https://github.com/projectcalico/canal/blob/master/k8s-install/canal.yaml

- commands:
https://www.digitalocean.com/community/tutorials/how-to-create-a-kubernetes-cluster-using-kubeadm-on-ubuntu-18-04


### Tested on:
 Ubuntu 18.04


## Deploy:
 fill hosts in hosts, specify ssh key in ansible.cfg then:
 
 **ansible-playbook deploy.yml**

 At the end, on a Master node will be file join.sh - run it to join nodes, when it needed


## Test

#### create service Nginx

 kubectl create deployment nginx --image=nginx
 
 kubectl expose deploy nginx --port 80 --target-port 80 --type NodePort

 kubectl get services
- this command will return node.port (nginx  NodePort  10.106.144.22   <none>  80:31511/TCP   2m23s)
- you can browse any node IP and this port to check all works fine

#### cleanup

 kubectl delete deployment nginx
 
 kubectl delete service nginx
