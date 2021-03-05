# Servicios de forma Imperativa
## Práctica 1:  Creación de servicios de forma Imperativa

*Ver objetos*

```bash
kubectl get deploy,pods,rs,svc
```

*YAML...*

```yml
apiVersion: apps/v1 # i se Usa apps/v1beta2 para versiones anteriores a 1.9.0
kind: Deployment
metadata:
  name: nginx-d # Nombre del Deployment
  labels:
    estado: "1"        
spec:
  selector:   #permite seleccionar un conjunto de objetos que cumplan las condicione
    matchLabels: # Para buscar objetos que tenga una determinada etiqueta
      app: nginx
  replicas: 2 # indica al controlador que ejecute 2 pods
  template:   # Plantilla que define los containers
    metadata:
      labels:
        app: nginx
    spec: #Hace referencia a los contenedores
      containers:
      - name: nginx
        image: nginx:1.7.9
        ports:
        - containerPort: 80
```

## Creamos el deploy

```bash
kubectl apply -f deploy_nginx.yaml
```

## Creamos el servicio 

```bash
kubectl expose deployment nginx-d --name=web --target-port=80 --type=NodePort
```

## Ver el servicio

```bash
kubectl get svc
kubectl get svc -o wide
kubectl describe svc web
```

## Ver la IP del cluster

```bash
minikube ip
```

## Buscamos el puerto del deployment

```bash
kubectl get svc -o wide
```
>Podemos observar la IP que le ha asignado al servicio dentro del clúster y el puerto por el que podemos acceder.

> Para acceder a los pods necesitamos la ip del cluster y el puerto

## Acceso desde el exterior

Ver lo que hemos creado
```bash
kubectl get deploy,pods,rs
```

```bash
curl 192.168.39.34:32532
firefox 192.168.39.34:32532
```

## Borramos el servicio anterior web

```bash
kubectl delete deploy nginx-d
kubectl delete svc web
```