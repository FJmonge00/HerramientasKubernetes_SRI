# Etiquetas

## Borramos los pods

```bash
kubectl delete pods --all
```

*YAML...*

```bash
apiVersion: v1
kind: Pod
metadata:
  name: tomcat
  labels:
    estado: "desarrollo"
    responsable: "juan"
spec:
  containers:
   - name: tomcat     
     image: tomcat
```

## Creamos el Pod

```bash
kubectl apply -f tomcat.yaml 
```

## Ver etiquetas

```bash
kubectl describe pod tomcat
kubectl get pods tomcat --show-labels
```