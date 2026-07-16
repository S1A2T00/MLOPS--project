# MLOPS--project
This is a mlops project
# 🚗 MLOps Project — Vehicle Insurance Data Pipeline

Welcome to this MLOps project, designed to demonstrate a robust, production-style pipeline for managing vehicle insurance data. This project showcases the tools, techniques, services, and features that go into building and deploying a real-world machine learning system — from raw data to a live, auto-deployed application.

![Python](https://img.shields.io/badge/Python-3.10-3776AB?style=flat-square&logo=python&logoColor=white)
![MongoDB](https://img.shields.io/badge/MongoDB-Atlas-47A248?style=flat-square&logo=mongodb&logoColor=white)
![AWS](https://img.shields.io/badge/AWS-S3%20%7C%20EC2%20%7C%20ECR%20%7C%20IAM-FF9900?style=flat-square&logo=amazonaws&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-Containerized-2496ED?style=flat-square&logo=docker&logoColor=white)
![CI/CD](https://img.shields.io/badge/CI%2FCD-GitHub%20Actions-2088FF?style=flat-square&logo=githubactions&logoColor=white)

---

## 📁 Project Setup and Structure

**Step 1: Project Template**
Execute `template.py` to generate the initial project skeleton — folder structure and placeholder files.

**Step 2: Package Management**
Configure `setup.py` and `pyproject.toml` so local packages can be imported across the project.
> 💡 Tip: See `crashcourse.txt` for a quick primer on how these files work.

**Step 3: Virtual Environment & Dependencies**
```bash
conda create -n vehicle python=3.10 -y
conda activate vehicle
pip install -r requirements.txt
```
Verify installation:
```bash
pip list
```

---

## 📊 MongoDB Setup and Data Management

**Step 4: MongoDB Atlas Configuration**
- Sign up for MongoDB Atlas and create a new project.
- Spin up a free **M0 cluster**, set a DB username/password, and whitelist access from anywhere (`0.0.0.0/0`).
- Grab the Python connection string and save it (swap in your `<password>`).

**Step 5: Pushing Data to MongoDB**
- Create a `notebook/` folder, add the dataset, and build `mongoDB_demo.ipynb`.
- Push the dataset to MongoDB from the notebook.
- Confirm the upload in **MongoDB Atlas → Database → Browse Collections**.

---

## 📝 Logging, Exception Handling & EDA

**Step 6: Logging & Exception Handling**
Build custom `logger` and `exception` modules and validate them via `demo.py`.

**Step 7: EDA & Feature Engineering**
Explore the dataset and engineer features inside the **EDA and Feature Engineering** notebook to prep it for the pipeline.

---

## 📥 Data Ingestion

**Step 8: Data Ingestion Pipeline**
- Define MongoDB connection logic in `configuration/mongo_db_connections.py`.
- Build the ingestion components inside `data_access/` and `components/data_ingestion.py` to fetch and transform the data.
- Update `entity/config_entity.py` and `entity/artifact_entity.py` with ingestion configs.
- Run `demo.py` after setting the MongoDB URL as an environment variable.

**Setting Environment Variables**
```bash
# Bash
export MONGODB_URL="mongodb+srv://<username>:<password>...."

# PowerShell
$env:MONGODB_URL = "mongodb+srv://<username>:<password>...."
```
> Note: On Windows, environment variables can also be set via System Settings.

---

## 🔍 Data Validation, Transformation & Model Training

**Step 9: Data Validation**
Define the dataset schema in `config/schema.yaml` and implement validation logic in `utils/main_utils.py`.

**Step 10: Data Transformation**
Implement transformation logic in `components/data_transformation.py` and add `estimator.py` to the `entity/` folder.

**Step 11: Model Training**
Build out `components/model_trainer.py`, powered by the estimator class defined in `estimator.py`.

---

## 🌐 AWS Setup for Model Evaluation & Deployment

**Step 12: AWS Setup**
- Log into the AWS Console and create an IAM user with **AdministratorAccess**.
- Set credentials as environment variables:
```bash
export AWS_ACCESS_KEY_ID="YOUR_AWS_ACCESS_KEY_ID"
export AWS_SECRET_ACCESS_KEY="YOUR_AWS_SECRET_ACCESS_KEY"
```
- Add these keys and the target region to `constants/__init__.py`.

**Step 13: Model Evaluation and Pushing to S3**
- Create an S3 bucket named `my-model-mlopsproj` in `us-east-1`.
- Implement model push/pull logic in `src/aws_storage` and `entity/s3_estimator.py`.

---

## 🚀 Model Evaluation, Model Pusher & Prediction Pipeline

**Step 14: Model Evaluation & Model Pusher**
- Implement the model evaluation and deployment components.
- Build the **Prediction Pipeline** and set up `app.py` for API integration.

**Step 15: Static & Template Directories**
Add `static/` and `templates/` directories to power the web UI.

---

## 🔄 CI/CD Setup with Docker, GitHub Actions & AWS

**Step 16: Docker and GitHub Actions**
- Create the `Dockerfile` and `.dockerignore`.
- Set up GitHub Actions, authenticating with AWS via GitHub Secrets:
  - `AWS_ACCESS_KEY_ID`
  - `AWS_SECRET_ACCESS_KEY`
  - `AWS_DEFAULT_REGION`
  - `ECR_REPO`

**Step 17: AWS EC2 and ECR**
- Spin up an EC2 instance for deployment.
- Install Docker on the EC2 machine.
- Connect the EC2 instance as a **self-hosted GitHub Actions runner**.

**Step 18: Final Steps**
- Open port `5080` on the EC2 instance's security group.
- Access your live app at `http://<public_ip>:5080`.

---

## 🛠️ Additional Resources

- **Crash Course on `setup.py` and `pyproject.toml`** — see `crashcourse.txt` for details.
- **GitHub Secrets** — used to manage credentials securely for CI/CD.

---

## 🎯 Project Workflow Summary

```
Data Ingestion ➔ Data Validation ➔ Data Transformation
      ➔ Model Training ➔ Model Evaluation ➔ Model Deployment
      ➔ CI/CD Automation via GitHub Actions, Docker, AWS EC2 & ECR
```

---

## 💬 Connect

If you found this project helpful or have any questions, feel free to reach out!

This README provides a structured walkthrough of the MLOps project — showcasing the end-to-end pipeline, cloud integration, CI/CD setup, and robust data handling capabilities.
