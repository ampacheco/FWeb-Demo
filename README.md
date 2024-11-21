# FWeb-Demo

Env Setup
```
```

Pod
````
apiVersion: v1
kind: Pod
metadata:
  name: secure-app
  labels:
    app: juiceshopapp
spec:
  containers:
  - image: "bkimminich/juice-shop"
    name: juiceshopapp-image
    ports:
    - containerPort: 3000
      protocol: TCP

---
apiVersion: v1
kind: Service
metadata:
  name: juiceshopapp
spec:
  selector:
    app: secure-app
  ports:
  - protocol: TCP
    port: 80
    targetPort: 3000
````

Service
````
apiVersion: v1
kind: Pod
metadata:
  name: secure-app
  labels:
    app: juiceshopapp
spec:
  containers:
  - image: "bkimminich/juice-shop"
    name: juiceshopapp-image
    ports:
    - containerPort: 3000
      protocol: TCP

---
apiVersion: v1
kind: Service
metadata:
  name: juiceshopapp
spec:
  selector:
    app: secure-app
  ports:
  - protocol: TCP
    port: 80
    targetPort: 3000
````

Ingress
````
apiVersion: v1
items:
- apiVersion: networking.k8s.io/v1
  kind: Ingress
  metadata:
    annotations:
      nginx.ingress.kubernetes.io/ssl-redirect: "false"
      nginx.ingress.kubernetes.io/use-regex: "true"
    creationTimestamp: "2024-11-19T01:35:38Z"
    generation: 1
    name: js-ingress
    namespace: default
    resourceVersion: "14634"
    uid: a960423f-baed-442e-85b0-5df3929d950b
  spec:
    ingressClassName: nginx
    rules:
    - http:
        paths:
        - backend:
            service:
              name: juiceshopapp
              port:
                number: 80
          path: /
          pathType: Prefix
````
