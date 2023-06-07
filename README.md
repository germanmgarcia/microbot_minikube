# microbot-minikube

## Crear los certificados y secrets

Para almacenar los certificados, debemos generarlos utilizando el siguiente comando:

```bash
openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout tls-key.key -out tls-cert.crt
```

## Activar el Addon Nginx Ingress en Minikube
```bash
minikube addons enable ingress
```

## Desplegar la imagen microbot y configurar un service para acceder al pod instanciado

```bash
kubectl create ns microbot
kubectl -f microbot-deployment.yaml apply
kubectl -f microbot-secret.yaml apply
kubectl -f microbot-service.yaml apply
kubectl -f microbot-ingress.yaml apply
```

## Añadir tu dominio a tu archivo hosts
```bash
sudo nano /etc/hosts
```
### Añadir 
```bash
192.168.49.2 microbot.minikube.io
```