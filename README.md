# 🚀 Yii2 Docker Swarm Deployment with Ansible, GitHub Actions & Monitoring

This project demonstrates a **complete DevOps pipeline** to deploy a **PHP Yii2 application** using:

- Docker Swarm on AWS EC2  
- NGINX (host-level reverse proxy)  
- Ansible for infrastructure config automation  
- GitHub Actions for CI/CD  
- Prometheus + Grafana + Node Exporter for monitoring()

---

## 📦 Tech Stack

| Tool            | Purpose                                      |
|-----------------|----------------------------------------------|
| PHP Yii2        | Web application framework                    |
| Docker + Swarm  | Containerization and service orchestration   |
| Ansible         | Infrastructure setup on EC2                  |
| GitHub Actions  | CI/CD automation                             |
| NGINX           | Host-based reverse proxy                     |
| Prometheus      | Metrics scraping and monitoring              |
| Grafana         | Visualization dashboard                      |
| Node Exporter   | EC2 system metrics exporter for Prometheus   |



## Deployment Steps

### Current CI/CD Workflow

1. **Code Push**  
   Whenever code is pushed to the `main` branch, the GitHub Actions workflow is automatically triggered.

2. **Docker Image Build & Push**  
   The workflow builds the Docker image for the Yii2 app and pushes it to Docker Hub or GitHub Container Registry.

3. **Ansible Playbook Execution**  
   After the image is pushed, the workflow SSHs into the EC2 instance and runs the Ansible playbook, which performs the Docker Swarm stack deployment (`docker stack deploy`) along with all necessary setup and configuration.

4. **Application Update**  
   The Docker Swarm stack is updated on the EC2 instance with the new image, and NGINX reverse proxy runs on the host.

---

### Notes

- **Docker stack deployment is currently managed inside the Ansible playbook.**  
- If needed, the Docker stack deploy command can be moved into the CI/CD workflow itself in the future for more granular control or faster deployment cycles.  

---

### Summary

| Trigger           | Action                                                |
|-------------------|-------------------------------------------------------|
| Push to `main`    | Build & push Docker image → Run Ansible playbook on EC2 → Docker Swarm stack deployment |
| Result            | Yii2 app is updated automatically via Docker Swarm managed by Ansible |

---

This setup ensures a fully automated pipeline from code commit to live deployment with infrastructure managed by Ansible.


