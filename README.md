# 🚀 End-to-End Machine Learning Project

This project demonstrates a full **Machine Learning Web Application** workflow including model prediction using Flask, containerization with Docker, and deployment to AWS EC2 using **GitHub Actions CI/CD** pipelines.

---

# 🎥 Demo

> 📺 **Watch the project in action:**  
> [[Watch Video Here](https://drive.google.com/file/d/1UaRAXpavmRXLuoK0jt8q6FpiepOG34t0/view?usp=sharing)]

---

# 📦 Project Structure

```
├── Dockerfile
├── app.py
├── requirements.txt
├── templates/
│   ├── index.html
│   └── home.html
├── src/
│   └── pipeline/
│       └── predict_pipeline.py
├── .github/
│   └── workflows/
│       └── main.yaml
└── README.md
```

---

# 🐳 Docker Setup on EC2

### (Optional but Recommended)
```bash
sudo apt-get update -y
sudo apt-get upgrade -y
```

### (Required - Install Docker)
```bash
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh get-docker.sh
sudo usermod -aG docker ubuntu
newgrp docker
```

---

# ⚙️ GitHub Actions CI/CD Pipeline

The project uses **GitHub Actions** for:

- ✅ **Continuous Integration:** Code linting and testing on every push to `master`
- ✅ **Continuous Delivery:** Building Docker images and pushing to AWS ECR
- ✅ **Continuous Deployment:** Deploying updated images from ECR to EC2 (self-hosted runner)

Workflow file:  
`.github/workflows/main.yaml`

---

# 🔒 GitHub Secrets Setup

Configure these secrets in your GitHub repository:

| Secret Name              | Value/Description                                          |
|---------------------------|-------------------------------------------------------------|
| `AWS_ACCESS_KEY_ID`        | Your AWS IAM Access Key ID                                 |
| `AWS_SECRET_ACCESS_KEY`    | Your AWS IAM Secret Access Key                             |
| `AWS_REGION`               | Your AWS Region (e.g., `us-east-1`)                        |
| `AWS_ECR_LOGIN_URI`        | Example: `566373416292.dkr.ecr.ap-south-1.amazonaws.com`    |
| `ECR_REPOSITORY_NAME`      | Name of your ECR Repository (e.g., `simple-app`)            |

---

# 🚀 Deployment Instructions

Once the GitHub Actions workflow is triggered:

1. Your code will be linted and tested.
2. A Docker image will be built and pushed to AWS ECR.
3. EC2 (self-hosted runner) will pull the latest image and run the container using:
    ```bash
    docker run -d -p 8080:8080 --ipc="host" --name=mltest [Image_Name]
    ```

Access the application on your EC2 Public IP at:
```
http://<EC2_PUBLIC_IP>:8080/
```

---

> **Tip:** 🔥 Always keep your AWS credentials safe and avoid hardcoding them!

---

# 🛠️ Tech Stack Used
- Python 3.8
- Flask
- Docker
- GitHub Actions
- AWS EC2
- AWS ECR
- HTML (Frontend Templates)
- Scikit-learn (Model)
