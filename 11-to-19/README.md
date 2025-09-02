### 11. find out the issue in the below Yaml (don't use AI)

```yaml
apiVersion: apps/v1
kind: ReplicaSet
metadata:
  name: replicaset-2
spec:
  replicas: 2
  selector:
    matchLabels:
      tier: frontend
  template:
    metadata:
      labels:
        tier: nginx #error (tier: frontend)
    spec:
      containers:
      - name: nginx
        image: nginx
```
---
### 12. find out the issue in the below Yaml (don't use AI)

apiVersion: apps/v1
kind: deployment #error (Deployment)
metadata:
  name: deployment-1
spec:
  replicas: 2
  selector:
    matchLabels:
      name: busybox-pod
  template:
    metadata:
      labels:
        name: busybox-pod
    spec:
      containers:
      - name: busybox-container
        image: busybox
        command:
        - sh
        - "-c"
        - echo Hello Kubernetes! && sleep 3600
---
### 13. find out the issue in the below Yaml (don't use AI)

apiVersion: v1 #error (apiVersion: apps/v1)
kind: Deployment
metadata:
  name: deployment-1
spec:
  replicas: 2
  selector:
    matchLabels:
      name: busybox-pod
  template:
    metadata:
      labels:
        name: busybox-pod
    spec:
      containers:
      - name: busybox-container
        image: busybox
        command:
        - sh
        - "-c"
        - echo Hello Kubernetes! && sleep 3600

### 14. what's command you use to know what Image name that running the deployment 
```bash
kubectl describe deployment <deployment name> | grep Image:
```
---

### 15. create deployment using following data :
Name: httpd-frontend;
Replicas: 3;
Image: httpd:2.4-alpine
```bash
k create deployment httpd-frontend --image httpd:2.4-alpine  --replicas 3
# deployment.apps/httpd-frontend created
```
---
### 16. replace the image to nginx777 with command directly 
```bash
k set image deployments httpd-frontend httpd=nginx777
# deployment.apps/httpd-frontend image updated
```
---
### 17. rollback to pervious version
```bash 
k rollout undo deployment httpd-frontend --to-revision 1
# deployment.apps/httpd-frontend rolled back
```
---
### 18. Create a Simple Web Application:
* Use a Dockerfile to create a simple web application (e.g., an Nginx server serving an HTML page).
* Build the Docker image and push it to DockerHub your private Account.
*Done*
---
### 19. Create a Deployment Using This Image:
* Deploy the Docker image from DockerHub to Kubernetes with a Deployment that has 3 replicas.
```bash
k create deployment go-app --image  abeerseada/go-app --replicas 3
```
![ Screenshot](https://github.com/abeerseada/k8s_lec2_task/blob/main/images/19.png)  
