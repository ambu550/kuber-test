# kuber-test
https://habr.com/ru/company/ruvds/blog/438982/
https://habr.com/ru/company/ruvds/blog/438984/



in front

npm install
npm start
npm build

docker-compose up -d


install

curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikube
minikube start
minikube kubectl -- get po -A
alias kubectl="minikube kubectl --"
kubectl get po -A
minikube dashboard


cd resource-manifests/
kubectl create -f sa-frontend-pod.yaml
kubectl get pods

kubectl get pod -l app=sa-frontend --show-labels


kubectl create -f service-sa-frontend-lb.yaml
kubectl get svc

minikube service sa-frontend-lb

kubectl apply -f sa-frontend-deployment.yaml


kubectl delete pod sa-frontend sa-frontend2

kubectl apply --cluster=minikube --filename=sa-frontend-deployment-green.yaml --record=true
kubectl rollout history deployment sa-frontend

kubectl rollout undo deployment sa-frontend --to-revision=1


kubectl apply -f sa-logic-deployment.yaml --record
kubectl apply -f sa-web-app-deployment.yaml --record
kubectl apply -f service-sa-web-app-lb.yaml

minikube stop




