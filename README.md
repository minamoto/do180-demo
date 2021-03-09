DO180 Demo
==============

(1) pod.yaml (Podのみ)
---
apiVersion: v1
kind: Pod
metadata:
  labels:
    app: hello-pod
  name: hello-pod
spec:
  containers:
  - image: quay.io/redhattraining/hello-world-nginx:v1.0
    name: hello-world-nginx
    ports:
    - containerPort: 8080
      protocol: TCP
---

(2) Deployのみ
oc create deployment hello-pod2 --image quay.io/redhattraining/hello-world-nginx:v1.0
oc get all
oc expose deploy hello-pod2 --port=8080
oc expose svc hello-pod2

(3) Deploy/Service
oc new-app --name hello-pod3 --docker-image quay.io/redhattraining/hello-world-nginx:v1.0 
oc get all
oc expose svc hello-pod3
oc get route

(4) Podをスケールアップ
oc scale --replicas=4 deploy/hello-pod3
