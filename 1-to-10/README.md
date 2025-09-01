### 1. create pod nginx with name my nginx direct from command don't use yaml file 
```bash
k run my-nginx --image nginx 
```
![ Screenshot](https://github.com/abeerseada/k8s_lec2_task/blob/main/images/1.png)  
---
### 2. create pod nginx with name my nginx command and use Image nginx123  direct from command don't use yaml file
```bash
k run my-nginx --image nginx123
```
![ Screenshot](https://github.com/abeerseada/k8s_lec2_task/blob/main/images/2.png)  
---
3- check the status and why it doesn't work 
```bash
k describe po my-nginx | tail -n 5
k get pod
```
```
 Failed to pull image "nginx123": failed to pull 
```
- because there is no *nginx123* image.
![ Screenshot](https://github.com/abeerseada/k8s_lec2_task/blob/main/images/3.png)
---
4- I need to know node name - IP - Image Of the POD
```bash
k get pod my-nginx -o wide
```
![ Screenshot](https://github.com/abeerseada/k8s_lec2_task/blob/main/images/4.png)
---
5- delete the pod 
```bash 
 k delete po my-nginx 
```
![ Screenshot](https://github.com/abeerseada/k8s_lec2_task/blob/main/images/5.png)
---
6- create another one with yaml file and use label
```bash
k run my-nginx --image nginx --labels tier=fe --dry-run=client -o yaml > 6.yaml
k apply -f 6.yaml 
```
![ Screenshot](https://github.com/abeerseada/k8s_lec2_task/blob/main/images/6.png)
---
7-create Riplicaset with 3 replicas using nginx Image 
![ Screenshot](https://github.com/abeerseada/k8s_lec2_task/blob/main/images/7.png)
```bash
k apply -f 7.yaml
```
![ Screenshot](https://github.com/abeerseada/k8s_lec2_task/blob/main/images/7-2.png)
---
8-scale the replicas to 5 without edit in the Yaml file
```bash
k edit rs nginx-rs 
```
![ Screenshot](https://github.com/abeerseada/k8s_lec2_task/blob/main/images/8.png)
---
9-Delete any one of the 5 pods and check what happen and explain 
![ Screenshot](https://github.com/abeerseada/k8s_lec2_task/blob/main/images/9.png)
- it will be deleted, but rs will create another pod immediatly.
10-Scale down the pods again to 2 without scale command use terminal  

![ Screenshot](https://github.com/abeerseada/k8s_lec2_task/blob/main/images/10.png)
```bash
k scale rs nginx-rs --replicas 2
```