# hello-app

**Hello World Application**

**Description**
This project showcases the deployment of a "Hello world!" application, with all processes automated using Ansible. The application is containerized with Docker, while Kubernetes is employed to orchestrate the deployment.

**Pre-reqs**

- Ubuntu - 22.04 with VM Virtual Box
- Docker - building an image & push to Docker Hub
- Minikube - kubernetes cluster
- Ansible - automation of installation & running the app

**Container**

Public container image is available on [DockerHub](https://hub.docker.com/repository/docker/livsv/hello-orange-app/general)

**How-to deploy:**
Pre-reqs in terminal:
- Docker login:
         - **docker login**

**Manual steps:**

- Build and Push the Docker image:
    - Build the Docker image for the application using the docker build command:
         - **docker build -t hello-orange .**
    - Tagging the docker image:
        - After the image is built, use the tag command:
            - **docker tag hello-orange livsv/hello-orange:v1.0**
    - Uploading the Image to Docker Hub:
         - **docker push livsv/hello-orange:v1.0**
     
- Starting the minikube cluster:
    - Required rule for starting minikube
         - **sysctl fs.protected_regular=0**
    - Start minikube:
         - **minikube start --force**

- Applying kubernetes configuration files:
    - Apply Kubernetes service:
        - **kubectl apply -f service.yaml**
    - Apply Kubernetes deployment:
        - **kubectl apply -f deployment.yaml**
    - Monitoring and check the configuration:
        - Get basic info about nodes
            - **kubectl get pod**
            - **kubectl describe ~pod_name~**
            - **kubectl get -o wide node** -> used to retrieve the internal_IP
         
**Using Ansible Script**
- Executing the Deployment
    - Run the ansible playbook using the command:
        - ansible-playbook deploy.yaml

