## Escalar Deployment respecto a las ETIQUETAS

**Añadimos la etiqueta**
*YAML...*

```yml
apiVersion: apps/v1 # i se Usa apps/v1beta2 para versiones anteriores a 1$
kind: Deployment
metadata:
  name: nginx-d
  label:
    estado: "1"
spec:
  selector:   #permite seleccionar un conjunto de objetos que cumplan las$
    matchLabels:
      app: nginx
  replicas: 5 # indica al controlador que ejecute 2 pods
  template:   # Plantilla que define los containers
    metadata:
      labels:
        app: nginx
    spec:
      containers:
      - name: nginx
        image: nginx:1.7.9
        ports:
        - containerPort: 80
```

```bash
kubectl apply -f deploy_nginx.yaml
kubectl scale deploy -l estado=1 --replicas=20
kubectl get  pods
# Ver el tiempo que lleva iniciado
```

<!-- *Probar otras las otras formas* -->