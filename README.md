# 🚀 Vehicle Data Processing and Model Deployment Project

Welcome to the **Vehicle Data Processing and Model Deployment** project! This project demonstrates a full-stack machine learning pipeline, covering data ingestion, validation, transformation, model training, and deployment using MongoDB, AWS, Docker, and CI/CD with GitHub Actions. This end-to-end solution ensures seamless data handling and model deployment, making it production-ready.

---

## 📂 **Project Structure**
```plaintext
├── src
│   ├── components
│   ├── configuration
│   ├── data_access
│   ├── entity
│   ├── pipeline
│   ├── utils
├── notebook
├── static
├── template
├── .github/workflows
├── .dockerignore
├── Dockerfile
├── requirements.txt
├── setup.py
├── pyproject.toml
├── app.py
```

---

## 🛠️ **Setup Instructions**
### 1. **Create Project Template**
- Run `template.py` to generate the project template.

### 2. **Setup Local Packages**
- Update `setup.py` and `pyproject.toml` to configure local package imports.
- For more info, refer to **crashcourse.txt**.

---

### 3. **Setup Virtual Environment**
```bash
conda create -n vehicle python=3.10 -y
conda activate vehicle
pip install -r requirements.txt
```
- Confirm installation:
```bash
pip list
```

---

## 🍃 **MongoDB Setup**
1. Sign up to **MongoDB Atlas** and create a new project.
2. Create a cluster (`M0` service).
3. Set up username, password, and network access (`0.0.0.0/0`).
4. Copy connection string for Python.
5. Create `mongoDB_demo.ipynb` in `notebook` folder and push data to MongoDB:
   - Use the connection string in the notebook.
   - Data can be viewed in MongoDB Atlas → Database → Browse Collections.

---

## 🪵 **Logging & Exception Handling**
- Add a logger and exception handler:
  - `logger.py` → Test with `demo.py`
  - `exception.py` → Test with `demo.py`

---

## 📊 **Data Ingestion**
1. Define connection in `configuration.mongo_db_connections.py`.
2. Create ingestion functions in `data_access/proj1_data.py`.
3. Add classes:
   - `DataIngestionConfig` → `entity/config_entity.py`
   - `DataIngestionArtifact` → `entity/artifact_entity.py`
4. Code ingestion logic in `components/data_ingestion.py`.
5. Set MongoDB URL:
```bash
export MONGODB_URL="mongodb+srv://<username>:<password>@<cluster-url>"
```

---

## ✅ **Data Validation & Transformation**
- Define schema in `config/schema.yaml`.
- Code validation logic in `components/data_validation.py`.
- Code transformation logic in `components/data_transformation.py`.
- Add model estimator in `entity/estimator.py`.

---

## 🏋️ **Model Training**
- Code training logic in `components/model_trainer.py`.

---

## ☁️ **AWS Setup**
1. Create IAM user with `AdministratorAccess`.
2. Set AWS credentials:
```bash
export AWS_ACCESS_KEY_ID="YOUR_KEY"
export AWS_SECRET_ACCESS_KEY="YOUR_SECRET"
```
3. Add AWS constants in `constants/__init__.py`:
```python
MODEL_EVALUATION_CHANGED_THRESHOLD_SCORE = 0.02
MODEL_BUCKET_NAME = "my-mlopsproj1-model"
MODEL_PUSHER_S3_KEY = "model-registry"
```
4. Configure AWS S3 access:
   - Create S3 bucket → Region: `us-east-1`
   - Code S3 connection in `aws_connection.py`.

---

## 📈 **Model Evaluation & Pushing**
- Implement model evaluation and pusher logic.
- Push the model to S3 bucket.

---

## 🌐 **Deployment Pipeline**
1. Create Dockerfile and `.dockerignore`.
2. Setup GitHub Actions:
   - Create secrets for AWS credentials.
   - Create ECR repository.
3. Build Docker image and push to ECR:
```bash
docker build -t vehicleproj .
docker tag vehicleproj:latest <your-ecr-uri>
docker push <your-ecr-uri>
```

---

## 💻 **EC2 Setup**
1. Create an EC2 instance:
   - Image: Ubuntu Server 24.04 (free tier)
   - Instance: T2 Medium (~3.5rs/hr)
2. Install Docker:
```bash
sudo apt-get update -y
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh get-docker.sh
sudo usermod -aG docker ubuntu
```

---

## 🚀 **Connect EC2 to GitHub Actions**
1. Set up GitHub self-hosted runner.
2. Connect to EC2 instance.
3. Confirm runner status.

---

## 🌍 **Expose App to Internet**
1. Open EC2 security group:
   - Port: `5080`
   - Source: `0.0.0.0/0`
2. Start app:
```bash
docker run -d -p 5080:5000 vehicleproj
```
3. Open browser:
```
http://<EC2-Public-IP>:5080
```

---

## 🧪 **Trigger CI/CD**
- Commit and push changes:
```bash
git add .
git commit -m "Initial commit"
git push origin main
```
- GitHub Actions will automatically trigger:
   - Build → Test → Deploy

---

## 📢 **Routes**
| Route           | Description                     |
|-----------------|---------------------------------|
| `/`             | Homepage                        |
| `/train`         | Start model training             |
| `/predict`       | Predict using the trained model  |

---

## 🎯 **Tech Stack**
- **Python** (3.10)
- **MongoDB Atlas**
- **AWS** (IAM, S3, EC2, ECR)
- **Docker**
- **GitHub Actions** (CI/CD)
- **Pandas, Scikit-Learn, NumPy**

---

## 🤝 **Contributing**
Feel free to fork this repository and submit a pull request. Contributions are always welcome!

---

## 📜 **License**
This project is licensed under the **MIT License**.

---

## 🌟 **Show Some Love**
If you found this helpful, please ⭐ this repository!

---

This README is structured to give a clean, professional, and organized impression to recruiters and visitors. Let me know if you'd like to tweak anything! 😎