
 Kubernetes Full-Stack Application

This project demonstrates the deployment of a full-stack application on a Kubernetes cluster, including a Node.js backend, a MongoDB database, and an Nginx frontend. The application is containerized using Docker and orchestrated with Kubernetes, using ConfigMaps for environment management and Persistent Volumes for data storage.

 Prerequisites

- Docker
- Kubernetes (Minikube or any Kubernetes cluster)
- kubectl

 Setup Instructions

1. Clone the repository:
   
2. Build and Push Docker Images:
   - Backend:
     bash
     cd Backend
     docker build -t dockerhub-username/node-backend .
     docker push dockerhub-username/node-backend
     
   - Frontend:
     cd ../Frontend
     docker build -t dockerhub-username/nginx-frontend .
     docker push dockerhub-username/nginx-frontend
     

3. Deploy to Kubernetes:
   bash
   cd ../k8s
   kubectl apply -f namespace.yaml
   kubectl apply -f mongo/
   kubectl apply -f backend/
   kubectl apply -f frontend/
   

4. Access the Application:
   - Find the NodePort for the Nginx service and access the frontend in your browser.
     bash
     minikube service nginx-svc -n fullstack-app
     

 Key Features

- Scalable: Easily scale the backend and frontend services using Kubernetes.
- Persistent Storage: MongoDB data persists even after pod restarts.
- Environment Management: ConfigMaps and Secrets securely manage environment variables.
