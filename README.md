# Setup of Wordpress through k8s
**clone this GitHub repository** <br/>
> `git clone https://github.com/sadiqueiqbal28/wordpress-with-kubernetes.git` <br/>
**change directory** <br/>
> `cd wordpress-with-kubernetes` <br/>
## Execute k8s commands <br/>
**create namespace** <br/>
> `kubectl apply -f namespace.yml` <br/>
### backend <br/>
**create configMaps and secrets** <br/>
> `kubectl apply -f backend/configmap.yml`  <br/>
> `kubectl apply -f backend/secrets.yml` <br/>
**create sevice** <br/>
> `kubectl apply -f backend/service.yml` <br/>
**create statefulset** <br/>
> `kubectl apply -f backend/statefulset.yml` <br/>
### frontend <br/>
**configure service** <br/>
> `kubectl apply -f frontend/service.yml` <br/>
**create deployment** <br/>
> `kubectl apply -f frontend/deployment.yml` <br/>
#### Since we are using CLusterIP service we need to forward the port to see in browser <br/>
> `sudo -E kubectl port-forward svc/wp-svc 80:80 -n prod --address=0.0.0.0` <br/>