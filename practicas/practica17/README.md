# Práctica 1:  Creación de servicios de forma Declarativa

## Partimos que tenemos desplegado el deployment

*YAML...*

>IMPORTANTE:
Selector coincide con el Deployment

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

### Creamos el deploy

```bash
kubectl apply -f deploy_nginx.yaml
```

## Desplegamos el servicio a partir de un fichero

*YAML...*

```yml
apiVersion: v1
kind: Service
metadata:
  name: web-svc
  labels:
     app: nginx 
spec:
  type: NodePort
  ports:
  - port: 80
    nodePort: 30002 # Aquí especificamos el puerto
    protocol: TCP
  selector:
     app: nginx #Es el que relaciona los contenedores y los pods y los despliegues
```

<!-- ```yml
apiVersion: apps/v1 # i se Usa apps/v1beta2 para versiones anteriores a 1$
kind: Deployment
metadata:
  name: nginx-d # Nombre del Deployment
  labels:
    estado: "1"
spec:
  selector:   #permite seleccionar un conjunto de objetos que cumplan las$
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
``` -->

```bash
kubectl apply -f web-svc.yaml
```

## Buscamos el puerto del deployment

```bash
minikube ip
kubectl get svc
```

>Podemos observar la IP que le ha asignado al servicio dentro del clúster y el puerto por el que podemos acceder.

> Para acceder a los pods necesitamos la ip del cluster y el puerto

## Acceso desde el exterior

Ver lo que hemos creado
```bash
kubectl get deploy,pods,rs
```

```bash
curl IP:PUERTO
firefox IP:PUERTO
```

## Añado replicas para la prueba disponibilidad

*YAML...*
>IMPORTANTE:
Selector coincide con el Deployment

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
  replicas: 4 # indica al controlador que ejecute 2 pods <-----------------------
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

## Aplicar configuración

```bash
kubectl apply -f deploy_nginx_V2.yaml
kubectl get pods
```
>[--------------------------->IMPORTANTE<------------------------]
- 
- 
## Borrar en orden de creación

```bash
kubectl get deploy,pods,svc #Ver
kubectl delete svc web-svc #Borrado
kubectl get deploy,pods,rs #Ver
kubectl delete deploy nginx-d #Borrado
kubectl get deploy,pods,rs #Ver
#Comprobación final de borrado
kubectl get deploy,pods,svc #Ver
```