# Pods - Modificar objetos

## Práctica 1: Crear un pod y obtener información de él.

```bash
kubectl create -f nginx.yaml
```

*Obtener YAML*
```bash
kubectl get pod nginx1 -o yaml
```

## Práctica 2: Modificar un pod en vivo

> **Es necesario lanzar el POD con Apply**

```bash
kubectl apply -f nginx.yaml
```
*Modificamos el YAML añadiendo etiquetas*

```bash
vi nginx.yaml
```

*Aplicamos los cambios*

```bash
kubectl apply -f nginx.yaml
```

*Ver cambios*

```bash
kubectl describe pod nginx1
```

__________________________________________________

[Volver al índice](../../README.md)
