# Healthcare Streamlit Application with Docker and Kubernetes

This project involves containerizing a Streamlit application using Docker, then deploying it on a Kubernetes cluster using deployment and service configuration files. The Dockerfile ensures that the application runs in a consistent environment, while the Kubernetes configuration files manage the deployment and networking aspects, making the application accessible to users.

## 1. Application (`app.py`)

The `app.py` file contains the Python code for the Streamlit application.

### Features:

- **Data Fetching**:
  - `fetch_patients()`: Retrieves 50 random patient records from an external API.
  - `fetch_facilities()`: Retrieves healthcare facility data from an external API.
- **Data Generation**:
  - `generate_healthcare_data(num_records)`: Generates random healthcare service data.
  - `generate_medication_data(num_records)`: Generates random medication data.
- **Data Transformation**:
  - `transform_patients(data)`: Transforms raw patient data into a structured format.
  - `assign_services_to_patients(patients, services)`: Assigns healthcare services to patients.
  - `assign_medications_to_patients(patients, medications)`: Assigns medications to patients.
- **Visualizations**:
  - Bar charts for service cost distribution, medication cost distribution, and service count by type.
  - A line chart for medication cost over time.

## 2. Docker Setup (`Dockerfile`)

The `Dockerfile` is used to containerize the Streamlit application. Here’s what it typically includes:

### Dockerfile Breakdown:

- **Base Image**: Specifies the base image (usually a Python image) to build upon.
- **Dependency Installation**: Installs the required Python packages.
- **Copy Application Files**: Copies the application files into the Docker image.
- **Port Exposure**: Exposes the necessary port for the Streamlit application.
- **Run Command**: Specifies the command to start the Streamlit app.

## 3. Kubernetes Deployment Configuration (`deployment.yaml`)

The `deployment.yaml` file is used to define the Kubernetes deployment. It includes:

### Deployment Breakdown:

- **Metadata**: Information such as the deployment name.
- **Spec**: Details about the replicas, Docker image to use, and the ports.
- **Containers**: Defines the container specifications, including image and ports.

## 4. Kubernetes Service Configuration (`service.yaml`)

The `service.yaml` file configures how the application is exposed to the network. It includes:

### Service Breakdown:

- **Metadata**: Information such as the service name.
- **Spec**: Details about the service type (ClusterIP, NodePort, or LoadBalancer) and the ports.

## Project Workflow

### 1. Building the Docker Image:

- Using the `Dockerfile`, create a Docker image of the Streamlit application.
- Command:
  ```bash
  docker build -t your-docker-image-name .
  ```

### 2. Pushing the Docker Image:

- Push the Docker image to a container registry (e.g., Docker Hub).
- Command:
  ```bash
  docker push your-docker-image-name
  ```

### 3. Deploying to Kubernetes:

- Apply the Kubernetes deployment and service configurations to deploy the application.
- Commands:
  ```bash
  kubectl apply -f deployment.yaml
  kubectl apply -f service.yaml
  ```

### 4. Accessing the Application:

- The Kubernetes service will expose the application, making it accessible via a network endpoint.

## Files Involved

- **`app.py`**: Contains the code for the Streamlit application.
- **`Dockerfile`**: Contains instructions to build the Docker image.
- **`deployment.yaml`**: Defines the Kubernetes deployment specifications.
- **`service.yaml`**: Configures the Kubernetes service for network exposure.

## Prerequisites

- Docker
- Kubernetes cluster (local or cloud-based)
- kubectl configured to interact with the cluster
- Docker Hub account (for pushing images)

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
