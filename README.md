# FWeb-Demo

Env Setup
```
```

Pod
````
````

Service
````
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
