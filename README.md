DO180 Demo


(1) Podのみ

```
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
```

(2) Deployのみ
```
oc create deployment hello-pod2 --image quay.io/redhattraining/hello-world-nginx:v1.0
```

(3) Deploy/Service (Kubernetes)
```
oc create deployment hello-pod3 --image quay.io/redhattraining/hello-world-nginx:v1.0
oc get all
oc expose deploy hello-pod3 --port=8080
oc expose svc hello-pod3
```

(3) Deploy/Service (OpenShift)
```
oc new-app --name hello-pod4 --docker-image quay.io/redhattraining/hello-world-nginx:v1.0 
oc get all
oc expose svc hello-pod4
oc get route
```

(4) Podをスケールアップ
```
oc scale --replicas=4 deploy/hello-pod4
```
