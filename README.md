Here's a **detailed** README without code but with step-by-step instructions for your **Crop Prediction Using RandomForest on AWS** project.  

---

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
- **Database:** AWS RDS (PostgreSQL/MySQL for storing predictions).  
- **Storage:** AWS S3 (for model storage).  
- **Deployment:** AWS EC2, AWS Lambda, API Gateway.  

---

# 🚀 **Deployment Guide (AWS Setup)**  

## **1️⃣ Deploy Machine Learning Model on AWS EC2**  

### **Step 1: Create & Configure an EC2 Instance**  
- Launch an **Ubuntu 22.04** EC2 instance.  
- Set up **security groups** to allow inbound traffic on **port 5000** for the Flask API and **port 22** for SSH access.  
- Connect to the instance using SSH.  

### **Step 2: Install Required Software**  
- Update system packages.  
- Install **Python, pip, Flask, scikit-learn, joblib, and boto3**.  

### **Step 3: Transfer Model & Application to EC2**  
- Upload the trained model file (`crop_prediction_model.pkl`) and Flask application files to EC2.  

### **Step 4: Start the Flask API**  
- Run the Flask application to serve crop predictions.  
- Configure the instance to **run the API on startup** for continuous availability.  

---

## **2️⃣ Set Up API with AWS Lambda & API Gateway**  

### **Step 1: Upload Model to AWS S3**  
- Create an **S3 bucket** and upload the trained **crop prediction model** (`crop_prediction_model.pkl`).  

### **Step 2: Create an AWS Lambda Function**  
- Configure a new **Lambda function** to load the model from S3 and process user input.  
- Set appropriate **memory, execution timeout, and permissions**.  
- Install required Python packages inside the Lambda environment.  

### **Step 3: Deploy API Gateway**  
- Create a **REST API** using AWS API Gateway.  
- Define a **POST method** linked to the Lambda function.  
- Enable **CORS** for cross-origin requests.  
- Deploy the API and generate a **public endpoint URL**.  

### **Step 4: Test API Endpoint**  
- Use **Postman or cURL** to send a POST request with soil parameters.  
- Verify that the API returns the correct predicted crop.  

---

## **3️⃣ Database Integration with AWS RDS**  

### **Step 1: Set Up AWS RDS**  
- Choose **PostgreSQL or MySQL** as the database.  
- Configure **security groups** to allow connections from the EC2 instance.  

### **Step 2: Store & Retrieve Predictions**  
- Store user inputs and predicted crops in an RDS table.  
- Implement a **logging mechanism** for future analysis.  

---

# 🎯 **Future Enhancements**  

- **Weather API Integration:** Fetch real-time weather data to improve accuracy.  
- **Mobile App Integration:** Provide farmers with an easy-to-use mobile interface.  
- **Deep Learning Models:** Explore CNNs or LSTMs for enhanced predictions.  
- **AutoML Optimization:** Use AutoML for hyperparameter tuning.  
- **Voice Assistant Feature:** Enable voice-based crop recommendations.  

---

# 📝 **Contributors**  

👨‍💻 **Kunal Aher Agriculture Tech**  

---

This **detailed README** provides a **step-by-step AWS deployment guide** for your **Crop Prediction System**. Let me know if you need additional details! 🚀
