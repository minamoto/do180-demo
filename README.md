# DO180 Demo


## (1) Podのみ

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

## (2) Deploy/Service (Kubernetes)
```
kubectl create deployment hello-pod2 --image quay.io/redhattraining/hello-world-nginx:v1.0
kubectl expose deployment hello-pod2 --port=8080
```

## (3) Deploy/Service (OpenShift)
```
oc new-app --name hello-pod3 --docker-image quay.io/redhattraining/hello-world-nginx:v1.0 
oc expose service hello-pod3
oc get route
```

## (4) Podをスケールアップ
```
oc scale --replicas=3 deployment/hello-pod3
```
