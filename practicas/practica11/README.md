# Selectores

*Ver TODAS LAS etiquetas*
```bash
kubectl get pods --show-labels
```
## Práctica 1:  Creación de objetos con diversas etiquetas

### Lanzamos los pods

```bash
kubectl apply -f tomcat1.yaml
kubectl apply -f tomcat2.yaml
kubectl apply -f tomcat3.yaml
```

[YAML Tomcat 1](./tomcat1.yaml)
[YAML Tomcat 2](./tomcat2.yaml)
[YAML Tomcat 3](./tomcat3.yaml)

*Ver TODOS LOS PODS con etiqueta DESARROLLO*

```bash
kubectl get pods --show-labels -l estado=desarrollo
```

*Ver TODOS LOS PODS con etiqueta TESTING*

```bash
kubectl get pods --show-labels -l estado=testing
```

*Ver TODOS LOS PODS **(CON AND)** con etiqueta Desarrollo y respondable*

```bash
kubectl get pods --show-labels -l estado=desarrollo,responsable=juan
```

*Ver TODOS LOS PODS **(CON OR Y NEGATIVO)** con etiqueta Desarrollo y respondable NO SEA JUAN*

```bash
kubectl get pods --show-labels -l responsable!=juan
```

*Ver TODOS LOS PODS **(CON in)** con etiqueta Desarrollo y respondable NO SEA JUAN*

```bash
kubectl get pods --show-labels -l 'estado in (desarrollo,testing)'
```

*Ver TODOS LOS PODS QUE NO SEAN **(CON not in)** con etiqueta Desarrollo y respondable NO SEA JUAN*

```bash
kubectl get pods --show-labels -l 'estado notin (desarrollo,testing)'
```

*BORRAR TODOS LOS PODS QUE SEAN DESARROLLO*

```bash
kubectl delete pods -l estado=desarrollo
```