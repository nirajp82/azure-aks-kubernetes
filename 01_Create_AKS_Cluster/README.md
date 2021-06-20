# Cloud Shell - Configure kubectl
* Login to Azure
  * az login

* Get access credentials for a managed Kubernetes cluster.
  * _az aks get-credentials --resource-group <Resource-Group-Name> --name <Cluster-Name>_
  
* List Kubernetes Worker Nodes
  * kubectl get nodes
  * kubectl get nodes -o wide

* List Namespaces
  * kubectl get namespaces
  * kubectl get ns

* List Pods from all namespaces
  * kubectl get pods --all-namespaces

* List all k8s objects from Cluster Control plane
  * kubectl get all --all-namespaces
  
* Deploy Sample Application and Test
  * kubectl apply -f kube-manifests/
  
* fetch details about pods
  * kubectl describe pod <Pod-Name>

* Verify Pods
  * kubectl get pods

* Verify Deployment
  * kubectl get deployment

* Verify Service (Make a note of external ip)
  * kubectl get service
  * Access Application
	* http://<External-IP-from-get-service-output>
  
* Delete Applications
  * kubectl delete -f kube-manifests/  
