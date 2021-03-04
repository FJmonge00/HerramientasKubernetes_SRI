# Pods de forma imperativa

## Práctica 1:  Crear pods de forma imperativa: nginx1 y nginx2

### Levantamos el pods
```bash
kubectl run nginx1 --image=nginx
```

![capturas](../../imagenes/crearpods.jpg)

### Estado del pod
```bash
kubectl get pods
```
![capturas](../../imagenes/estadoPods.jpg)

### Levantamos un segundo pod
```bash
kubectl run nginx2 --image=nginx
```

### Estado del pod
```bash
kubectl get pods
```

![capturas](../../imagenes/otroPod.jpg)

### Información detallada del pod
```bash
kubectl describe pod nginx2
```

![capturas](../../imagenes/detallada.jpg)

### Ejecutar un comando dentro del pod

```bash
kubectl exec nginx2 -- ls
```
### Ejecutar un comando de manera interactiva en un contenedor de un pod

```bash
kubectl exec nginx2 -it -- bash
```

![capturas](../../imagenes/dentrodelcontenedor.png)

## Práctica 2:  Crear un pod que contenga un servidor apache.

### Levantamos el pods

```bash
kubectl run apache --image=httpd
```

### Ver logs

```bash
kubectl logs apache
```

### Estado del pod
```bash
kubectl get pods
```

### Ejecutar un comando de manera interactiva en un contenedor de un pod

```bash
kubectl exec apache -it -- bash
```

![capturas](../../imagenes/accesoapache.png)

### Acceso a la web

```bash
curl localhost
```

## Práctica 3:  Comprobar el clúster con kubectl proxy

### Establecer una conexión con kubernetes

```bash
kubectl proxy
```

### Estado de kubernetes

```bash
firefox http://127.0.0.1:8001/healthz
```

### APIS

```bash
http://127.0.0.1:8001/api/v1/namespaces/default
```

![capturas](../../imagenes/apis.jpg)

### PODS

```bash
http://127.0.0.1:8001/api/v1/namespaces/default/pods
```

![capturas](../../imagenes/apis.jpg)

### POD de apache

```bash
http://127.0.0.1:8001/api/v1/namespaces/default/pods/apache
```

![capturas](../../imagenes/apachePod.jpg)

## OTROS APUNTES

### Acceso al cluster

```bash
minikube ssh
# Dentro docker ps
```

![capturas](../../imagenes/contenedoresCLuster.jpg)

__________________________________________________

[Volver al índice](../../../README.md)