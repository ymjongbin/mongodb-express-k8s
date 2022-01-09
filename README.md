# mongodb-express-k8s

<h3>Design Architecture </h3>
<p>Here is a diagram that we want to implement example of Microservice with Kubernetes, MongoDB, MongoDB Express & ArgoCD</p>
<img src="images/design-architecture.png"
     alt="Markdown Monster icon"
     style="float: left; margin-right: 10px;" />
<p>.</p>
<h3>ArgoCD Application </h3>
<p>Automates the deployment of the desired application states in the specified target environments</p>

<p>.</p>
<img src="images/argocd-application.png"
     alt="Markdown Monster icon"
     style="float: left; margin-right: 10px;" />

| Requirements      | Description |
| ---- | --- |
| ArgoCD install           | [Getting Start](https://argo-cd.readthedocs.io/en/stable/getting_started/)       |
| Mongo DB Express        | [ Environnement Variable](https://github.com/mongo-express/mongo-express)        |
<h3>MongoDB Express UI </h3>
<p></p>
<p>Web-based MongoDB admin interface, written with Node.js and express</p>
<img src="images/mongoDB-express.png"
     alt="Markdown Monster icon"
     style="float: left; margin-right: 10px;" />
<p>.</p>
<h3>   </h3>
<h3> How to run it in local </h3>
<ol>
  <li>RUN <b>Docker Desktop</b> for running <b>Docker</b> and <b>Kubenetues</b></li>
  <li>kubectl create namespace argocd</li>
  <li>kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml</li>
  <li>kubectl patch svc argocd-server -n argocd -p '{"spec": {"type": "LoadBalancer"}}'</li>
  <p><b>Get ArgoCD admin password</b></p>
  <li>kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d; echo</li>
  <p><b>WAIT UNTIL all pods running state</b></p>
  <li>kubectl get all -n argocd</li>
  <li>kubectl port-forward svc/argocd-server -n argocd 8080:443</li>
  <li><b>Launching Chrome and access http://localhost:8080</b></li>
  <li><b>Login ID: admin, password: output of #5</b></li>
  <li>kubectl get all -n argocd</li>
  <p><b>Running Kubenetues project</b></p>
  <li>kubectl apply -f application.yaml</li>
  <p><b>Watch ArgoCD's application, wait until all containers are running without problem</b></p>
  <li><b>To access Mongo Express http://localhost:8081</b></li>
</ol>

<h3> How to clean up all of containers</h3>
<ol>
     <p>kubectl delete all --all --namespace=argocd</p>
</ol>

