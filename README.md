# mongodb-express-k8s

<h3>Design Architecture </h3>
<p>Here is a diagram that we want to implement example of Microservice with Kubernetes, MongoDB, MongoDB Express & ArgoCD</p>
<img src="images/design-architecture.png"
     alt="Markdown Monster icon"
     style="float: left; margin-right: 10px;" />
<p>.</p>
<h3>ArgoCD Application </h3>
<p>Automates the deployment of the desired application states in the specified target environments</p>
<p>when a developer pushes application code to their git repository, the CI builds the code and a container image is built and registered to the container registry. Then, they push the manifests and Argo CD applies them to a Kubernetes cluster.</p>
<img src="images/argocd-application.png"
     alt="Markdown Monster icon"
     style="float: left; margin-right: 10px; margin-top: 20px;" />

| Requirements      | Description |
| ---- | --- |
| ArgoCD install          | [Getting Start](https://argo-cd.readthedocs.io/en/stable/getting_started/)       |
| Mongo DB Express        | [ Environnement Variable](https://github.com/mongo-express/mongo-express)        |
<h3>MongoDB Express UI </h3>
<p></p>
<p>Web-based MongoDB admin interface, written with Node.js and express</p>
<img src="images/mongoDB-express.png"
     alt="Markdown Monster icon"
     style="float: left; margin-right: 10px; margin-top: 20px;" />
<p>.</p>
<h3>   </h3>
<h3> How to run it in local </h3>

<p>RUN <b>Docker Desktop</b> for running <b>Docker</b> and <b>Kubenetues</b></p>

```bash
kubectl create namespace argocd
```
```bash
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
```

```bash
kubectl patch svc argocd-server -n argocd -p '{"spec": {"type": "LoadBalancer"}}'
```

<p><b>Get ArgoCD admin password</b></p>

```bash
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d; echo
```
<p><b>WAIT UNTIL all pods running state</b></p>

```bash
kubectl get all -n argocd
```
```bash
kubectl port-forward svc/argocd-server -n argocd 8080:443
```
<p><b>Launching Chrome and access ArgoCD server</b></p>

```bash
http://localhost:8080
```
<p><b>Login ID: admin, password: output of admin password</b></p>

```bash
kubectl get all -n argocd
```
<p><b>Running Kubenetues project</b></p>

```bash
kubectl apply -f application.yaml
```

<p><b>Watch ArgoCD's application, wait until all containers are running without problem</b></p>
<p>To access Mongo Express container</p>

```bash
http://localhost:8081
```

<h3> How to clean up all of containers</h3>

```bash
kubectl delete all --all --namespace=mongo
```
```bash
kubectl delete all --all --namespace=argocd
```
