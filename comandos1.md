Comandos minikube

```bash
minikube --help
# Ver estado del cluster actual
minikube status
# Ver IP del cluster actual
minikube ip
# Ver logs
minikube logs
# Conectarse al cluster actual
minikube ssh
# Dentro de la maquina
# cat /etc/os-release
minikube dashboard
# crear un clúster
minikube start -p cluster-pruebas
# Ver con que cluster ACTUAL esta trabajando
minikube start -p cluster-pruebas
# Ver listado clústers
minikube profile list
# cambiar cluster de trabajo
minikube profile cluster-pruebas
# Parar cluster virtual
minikube stop
# Eliminar cluster Kubernetes
minikube delete
```

Configuraciones


```bash
cat $HOME/.kube/config
cat $HOME/.minikube/machines
```