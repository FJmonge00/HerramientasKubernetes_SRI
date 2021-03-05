# Anotaciones

## Práctica 1:  Creación de objetos con diversas anotaciones

*YAML...*

```yml
apiVersion: v1
kind: Pod
metadata:
  name: tomcat4
  labels:
    estado: "produccion"
    responsable: "pedro"
  annotations:
    doc: "Se debe compilar con gcc"
    adjunto: "ejemplo de anotacion"
spec:
  containers:
   - name: tomcat     
     image: tomcat
```

## Lanzamos los PODs

```bash
kubectl apply -f tomcat4.yaml
```

## Ver anotaciones

```bash
kubectl describe pod tomcat4
```
### Ver desde el Dashboard

```bash
minikube dashboard
```