# **Real Estate Price Prediction Website**

This project focuses on developing a fully functional real estate price prediction website, starting from building a predictive model and ending with deploying the website in the cloud. It follows a systematic approach:

## **Model Creation:** 
The initial phase uses the Bangalore home prices dataset from Kaggle to build a prediction model using Python's `sklearn` and linear regression.

## **Backend Development:** 
A Python Flask server is created to host the model, which will handle HTTP requests.

## **Frontend Creation:** 
The user-facing website is developed using HTML, CSS, and JavaScript, allowing users to input details like home square footage and number of bedrooms. These inputs are sent to the Flask server, which returns the predicted home price.

During the model creation process, key data science concepts are addressed, including:

- Data loading and cleaning
- Outlier handling
- Feature engineering
- Dimensionality reduction
- Hyperparameter tuning with `GridSearchCV`
- K-fold cross-validation

### **Tools and Technologies Used:**

- **Python** for the backend and model
- **Numpy & Pandas** for data handling and cleaning
- **Matplotlib** for visualization
- **Sklearn** for machine learning model building
- **Jupyter Notebook, VS Code, and PyCharm** as development environments
- **Flask** for building the HTTP server
- **HTML, CSS, and JavaScript** for creating the website interface

---

## **Deployment Instructions (AWS EC2)**

### **Create an EC2 Instance:**
Use Amazon’s console to spin up an EC2 instance. Be sure to configure the security group to allow HTTP traffic.

### **Connect to EC2:**
Use SSH to connect to your instance. Here's an example command:
```bash
ssh -i "path_to_your_key.pem" ubuntu@your_ec2_public_dns
---


### **Nginx Setup:**

Install and start Nginx with the following:
```bash
sudo apt-get update
sudo apt-get install nginx
sudo service nginx start
Check the status with:
```bash
sudo service nginx status

### **Transfer Project Files:**
Use Git or WinSCP to upload your project to the EC2 instance at /home/ubuntu/your_project_folder.

### **Configure Nginx:**
Create an Nginx configuration file at /etc/nginx/sites-available/your_project.conf with this content:
server {
    listen 80;
    server_name your_project;
    root /home/ubuntu/your_project_folder/client;
    index app.html;
    location /api/ {
        proxy_pass http://127.0.0.1:5000;
    }
}

Enable the configuration by running:
sudo ln -s /etc/nginx/sites-available/your_project.conf /etc/nginx/sites-enabled/
sudo unlink /etc/nginx/sites-enabled/default
sudo service nginx restart

### **Install Dependencies and Start the Flask Server::**
sudo apt-get install python3-pip
sudo pip3 install -r /home/ubuntu/your_project_folder/server/requirements.txt
python3 /home/ubuntu/your_project_folder/server.py


### **Access the Website::**
Open your EC2 instance URL in a browser, and your website should be live and fully functional!










