# Setup of Wordpress through k8s
**clone this GitHub repository**
> `git clone https://github.com/sadiqueiqbal28/wordpress-with-kubernetes.git`
**change directory**
> `cd wordpress-with-kubernetes`
## Execute k8s commands
**create namespace**
> `kubectl apply -f namespace.yml`
### backend
**create configMaps and secrets**
> `kubectl apply -f backend/configmap.yml`
> `kubectl apply -f backend/secrets.yml`
**create sevice**
> `kubectl apply -f backend/service.yml`
**create statefulset**
> `kubectl apply -f backend/statefulset.yml`
### frontend
**configure service**
> `kubectl apply -f frontend/service.yml`
**create deployment**
> `kubectl apply -f frontend/deployment.yml`
#### Since we are using CLusterIP service we need to forward the port to see in browser
> `sudo -E kubectl port-forward svc/wp-svc 80:80 -n prod --address=0.0.0.0`