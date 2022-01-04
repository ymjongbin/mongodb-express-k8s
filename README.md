# mongodb-express-k8s

<h3>MongoDB Express UI </h3>
<p></p>
<p>Web-based MongoDB admin interface, written with Node.js and express</p>
<img src="images/mongoDB-express.png"
     alt="Markdown Monster icon"
     style="float: left; margin-right: 10px;" />
<p>.</p>
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

<h3> Clean up resources  </h3>
$kubectl delete all --all --namespace=mongo