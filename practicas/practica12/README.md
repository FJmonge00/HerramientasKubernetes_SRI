# Etiquetas REVISAR TAREA
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



*Ver TODOS LOS PODS con etiqueta DESARROLLO*

```bash
kubectl get pods --show-labels -l estado=desarrollo
```

*Ver TODOS LOS PODS con etiqueta TESTING*

```bash
kubectl get pods --show-labels -l estado=testing
```

*Ver TODOS LOS PODS (CON AND) con etiqueta Desarrollo y respondable*

```bash
kubectl get pods --show-labels -l estado=desarrollo,responsable=juan
```

*Ver TODOS LOS PODS (CON OR Y NEGATIVO) con etiqueta Desarrollo y respondable NO SEA JUAN*

```bash
kubectl get pods --show-labels -l responsable!=juan
```

*Ver TODOS LOS PODS (CON in) con etiqueta Desarrollo y respondable NO SEA JUAN*

```bash
kubectl get pods --show-labels -l 'estado in (desarrollo,testing)'
```

*Ver TODOS LOS PODS QUE NO SEAN (CON not in) con etiqueta Desarrollo y respondable NO SEA JUAN*

```bash
kubectl get pods --show-labels -l 'estado notin (desarrollo,testing)'
```

*BORRAR TODOS LOS PODS QUE SEAN DESARROLLO (CON not in) con etiqueta Desarrollo y respondable NO SEA JUAN*

```bash
kubectl delete pods -l estado=desarrollo
```

### Ver desde el Dashboard

```bash
minikube dashboard
```
![Imágen](../../imagenes/)