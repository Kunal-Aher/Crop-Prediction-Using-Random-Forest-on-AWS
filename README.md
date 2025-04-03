
# 🌾 **Crop Prediction Using RandomForest on AWS**  

## 📌 **Overview**  
This project predicts the most suitable crop for a given set of soil and environmental conditions using **Random Forest Classifier**. The model is deployed on **AWS**, providing scalable and real-time crop recommendations for farmers.  
![image](https://github.com/user-attachments/assets/5b5b29de-2082-4627-9682-ca800b7f255d)

---

## ✅ **Features**  

- **Accurate Predictions:** Uses RandomForestClassifier for high accuracy.  
- **Handles Missing Data:** Can handle missing values and noisy data.  
- **Cloud Deployment:** Deployed on AWS for global accessibility.  
- **User-Friendly UI:** Farmers can easily enter soil conditions.  
- **API-Based System:** Supports integration with mobile & web apps.  

---

## 📊 **Dataset Details**  

The dataset includes key soil nutrients and climate parameters:  

- **Nitrogen (N):** Essential for plant growth.  
- **Phosphorus (P):** Aids root development.  
- **Potassium (K):** Enhances drought resistance.  
- **Temperature (°C):** Determines crop viability.  
- **Humidity (%):** Affects water absorption.  
- **Soil pH:** Influences nutrient availability.  
- **Rainfall (mm):** Affects soil moisture content.  

Each sample in the dataset is labeled with the **most suitable crop** based on these parameters.  

---

## ⚙️ **Technology Stack**  

- **Machine Learning:** scikit-learn (RandomForestClassifier).  
- **Backend:** Flask (REST API for crop predictions).  
- **Frontend:** HTML, CSS, JavaScript (Bootstrap).  
- **Deployment:** AWS EC2, API Gateway.  

---

# 🚀 **Deployment Guide (AWS Setup)**  

## **1️⃣ Deploy Machine Learning Model on AWS EC2**  

### **Step 1: Create & Configure an EC2 Instance**  
- Launch an **Ubuntu 22.04** EC2 instance.  
- Set up **security groups** to allow inbound traffic on **port 8080** for the Flask API and **port 22** for SSH access.  
- Connect to the instance using SSH.  

### **Step 2: Install Required Software**  
- Update system packages.  
- Install **Python, pip, Flask, scikit-learn, pickle **.  

### **Step 3: Transfer Model & Application to EC2**  
- Upload the trained model file (`crop_prediction_model.pkl`) and Flask application files to EC2.  

### **Step 4: Start the Flask API**  
- Run the Flask application to serve crop predictions.  
- Configure the instance to **run the API on startup** for continuous availability.  

Here’s a step-by-step guide to **deploy your Crop Prediction System using EC2** instead of S3:

---

# 🚀 **AWS EC2 Deployment Guide for Crop Prediction System**

This guide walks you through **creating an EC2 instance, configuring it, and deploying your Flask-based ML model**.

---

## 🏗 **Step 1: Create an EC2 Instance**

1. **Log in to AWS Console** → Go to **EC2 Dashboard**.
2. **Launch a New Instance**:
   - Select **Ubuntu 22.04 LTS** (recommended).
   - Choose an instance type (**t2.micro** for free tier or a higher spec if needed).
3. **Configure Security Group**:
   - **SSH (port 22)** → Allow from your IP (or anywhere if needed).
   - **HTTP (port 80)** → Allow from anywhere (for public access).
   - **Custom TCP (port 5000 or 8080)** → Allow from anywhere (for Flask API).
4. **Key Pair**:
   - Create/download a **key pair (.pem file)** for SSH access.
5. **Launch Instance**.

---

## 🔗 **Step 2: Connect to EC2 via SSH**
1. Open **terminal** (Linux/Mac) or **Putty** (Windows).
2. Run:
   ```bash
   ssh -i your-key.pem ubuntu@your-ec2-public-ip
   ```
3. If using **Windows**, use **Putty** (convert `.pem` to `.ppk` via PuttyGen).

---

## ⚙️ **Step 3: Install Dependencies on EC2**
Run these commands after SSH-ing into EC2:

```bash
# Update system packages
sudo apt update && sudo apt upgrade -y

# Install Python and required packages
sudo apt install python3 python3-pip -y

# Install Flask and ML dependencies
pip3 install flask scikit-learn pandas joblib
```

---

## 📤 **Step 4: Transfer Model & Code to EC2**
Use **WinSCP (Windows)** or **scp (Linux/Mac)**:

```bash
scp -i your-key.pem -r /local-path-to-project ubuntu@your-ec2-public-ip:/home/ubuntu/
```

If using **WinSCP**:
1. Open WinSCP → Enter **EC2 Public IP, username (`ubuntu`)**, and select your **key**.
2. Transfer files (`app.py`, `model.pkl`, etc.).

---

## 🚀 **Step 5: Run Flask API on EC2**
1. **Navigate to your project directory**:
   ```bash
   cd /home/ubuntu/project-folder
   ```
2. **Run Flask API**:
   ```bash
   python3 app.py
   ```
3. If running on **port 5000**, access it at:
   ```
   http://your-ec2-public-ip:5000/
   ```
4. If the app should always run:
   ```bash
   nohup python3 app.py &
   ```

---

## 🌍 **Step 6: Make Flask API Publicly Accessible**
1. Edit `app.py` to:
   ```python
   app.run(host="0.0.0.0", port=5000)
   ```
2. Restart Flask:
   ```bash
   python3 app.py
   ```

---

## 🔄 **Step 7: Set Up Auto-Start on Boot (Optional)**
1. Open **crontab**:
   ```bash
   crontab -e
   ```
2. Add:
   ```
   @reboot cd /home/ubuntu/project-folder && nohup python3 app.py &
   ```

---

## ✅ **Step 8: Test API**
Send a **POST request**:
```bash
curl -X POST http://your-ec2-public-ip:5000/predict -H "Content-Type: application/json" -d '{"N":30, "P":60, "K":40, "temperature":25, "humidity":80, "ph":6.5, "rainfall":200}'
```

---

## 🔧 **Troubleshooting**
- **Port not accessible?** → Check **security group** settings.
- **App crashes?** → Check logs:
  ```bash
  tail -f nohup.out
  ```
- **Need HTTPS?** → Use **NGINX + SSL**.

---
# 📝 **Contributors**  

👨‍💻 **Kunal Aher**  

---

# 🎯 **Conclusion**
This guide covers **full deployment on EC2 without S3**. Let me know if you need refinements! 🚀

---


