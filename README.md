
 1. Run the App Locally
node app.js
Visit: http://localhost:5000

2. Build Docker Image
docker build -t s223986848/week06 .
3. Push to Docker Hub

docker push s223986848/week06:latest
4. Deploy to Kubernetes

kubectl apply -f kubernetes/deployment.yaml
kubectl apply -f kubernetes/service.yaml

5. Verify the Deployment

kubectl get pods
kubectl get svc

6. Port Forwarding

kubectl port-forward service/web-service 8080:80
Now visit: http://localhost:8080

7. Modify App


2. Rebuild and Push New Image

docker build -t s223986848/week06:v2 .
docker push s223986848/week06:v2
3. Update Deployment YAML
Edit kubernetes/deployment.yaml:
containers:
  - name: web
    image: s223986848/week06:v2
4. Apply Updated Deployment
kubectl apply -f kubernetes/deployment.yaml
Kubernetes Dashboard
You can access the Kubernetes dashboard via Docker Desktop or by:
kubectl proxy
