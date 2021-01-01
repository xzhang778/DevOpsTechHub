#### To start the Dashboard Service and Login
Reference Link: https://github.com/kubernetes/dashboard

kubectl apply -f RoleBinding.yaml

kubectl apply -f Service Account.yaml

//Get Bearer token
kubectl -n kubernetes-dashboard describe secret $(kubectl -n kubernetes-dashboard get secret | grep admin-user | awk '{print $1}')

//Start Dashboard UI Service and UI web
kubectl proxy

//Access the Dashboard and use Bearer token to login
http://localhost:8001/api/v1/namespaces/kubernetes-dashboard/services/https:kubernetes-dashboard:/proxy/


