# ⭐Node.js CI/CD with Jenkins, Docker & AWS EC2⭐

An awesome task that helped me understand how to set up a complete CI/CD Pipeline using Jenkins, Docker, and AWS EC2.

## 🔹About the Project

Setting up Jenkins and Docker on an EC2 instance to automate the deployment of a Node.js app through CI/CD pipelines.
A great hands-on task to understand:

✅ AWS EC2 basics

✅ Jenkins pipeline setup

✅ Docker & Docker Compose for app deployment

✅ GitHub Webhooks for automation

## 🔹Built With
This project uses:
 1. AWS EC2
 2. Jenkins
 3. Docker & Docker Compose
 4. Node.js Application
 5. GitHub Webhook Integration

 ## 🔹Quick Setup Guide
1️⃣ Launch EC2 Instance
  * Create an EC2 instance with required permissions.
  * Allow ports 22, 8080, and 8000 in the security group.
  * Note the public IP address of your instance.

2️⃣ Install Jenkins, Docker & Docker Compose
    Use the following guides to install:
  * [Jenkins Installation](https://www.jenkins.io/doc/book/installing/)
  * [Docker Installation](https://docs.docker.com/get-started/get-docker/)
  * [Docker-compose Installation](https://docs.docker.com/compose/install/)


3️⃣ Fork and Clone the Repository
   On your EC2 instance, run:
  ```
   git clone https://github.com/Gayatrishinde21/node-todo-cicd.git
   cd node-todo-cicd
  ```

4️⃣ Create SSH Keys
   Generate SSH keys on your EC2:
   ```
   ssh-keygen
   cat ~/.ssh/id_rsa.pub
   ```
Add this public key to your GitHub SSH keys.

5️⃣ Configure GitHub
  * Go to Settings → SSH and GPG Keys in GitHub, add your EC2 public key.
  * In your repository settings, add a Webhook:
  * ```
     http://<your_ec2_public_ip>:8080/github-webhook/
    ```
  * Set Content Type to application/json.

6️⃣ Configure Jenkins
  * Install the GitHub Integration Plugin in Jenkins.
  * Create a Freestyle Project
  * Add your GitHub project URL.
  * Configure Git credentials if required.
  * Enable GitHub hook trigger for GITScm polling.

7️⃣ Jenkins CI/CD Steps
   In your Jenkins project:
  * Add build steps to run
  ```
   docker build . -t node-app-todo
   docker run -d --name node-app-container -p 8000:8000 node-app-todo
```
This builds and deploys your Node.js app inside containers.

8️⃣ Check Webhook Connection
   * In GitHub repo → Settings → Webhooks
   * Look for a green checkmark indicating a successful connection.

9️⃣ Run the Pipeline
   * In Jenkins, click Build Now.
   * Jenkins will pull code, build containers, and deploy your app.

🔟 Access the Application
   Visit:
   ```
   http://<your_ec2_public_ip>:8000
   ```

You should see your running Node.js application. 🎉

## 💡 Usage

You can make code changes and push to GitHub — Jenkins will automatically deploy the new version using the CI/CD pipeline.
