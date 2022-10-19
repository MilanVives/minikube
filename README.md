### Deployment file toepassen
kubectl apply -f appdelpoyment.yml

### Service

type: NodePort 
....
nodePort: 31500 (moet tussen 30000 en 32767 zijn)

### Service toepassen (selector moeyt identiek zijn aan selector van de pods zie deployment file)
kubectl apply -f appservice.yml

# Vanaf nu is je service bereikbaar op het ip adres van je node port 31500

# IP adres node vinden:

# manier 1: 
minikube ip

milan⚡️~/Dev/Docker/k8s/minik8s$minikube ip
192.168.49.2


# manier 2:
kubectl get -o wide nodes


milan⚡️~/Dev/Docker/k8s/minik8s$kubectl get -o wide nodes
NAME       STATUS   ROLES           AGE    VERSION   INTERNAL-IP    EXTERNAL-IP   OS-IMAGE             KERNEL-VERSION      CONTAINER-RUNTIME
minikube   Ready    control-plane   127m   v1.25.2   192.168.49.2   <none>        Ubuntu 20.04.5 LTS   5.15.0-50-generic   docker://20.10.18

# in de browser surfen naar http://192.168.49.2:31500/