# ⚙️ Tomcat

Tomcat is also a **web server** where we can deploy web applications.

---

## 🔄 Alternative Tools

Some alternative tools are:

1. Nginx
2. HTTPD
3. Caddy
4. Jetty

---

# 🚀 How to Deploy a `.war` (Web Archive) File into Tomcat Server

The basic deployment flow is:

```text
       🛠️ Maven Instance
              │
              │
           .war file
              │
              │ SSH Connection
              ▼
       ⚙️ Tomcat Instance
              │
              ▼
       Deploy .war file
              │
              ▼
        🌐 Web Application

# 🛠️ Steps to Deploy a .war File in Tomcat

## 1️⃣ Launch Two EC2 Instances

Launch 2 instances:

- One instance for Maven
- One instance for Tomcat

## 2️⃣ Connect to Maven Instance

Connect to the Maven instance and install:

- Java
- Maven

**Commands**
sudo apt update
sudo apt install openjdk-17-jdk -y
sudo apt install maven -y


Clone the spring-petclinic-framework repository.

git clone <spring-petclinic-framework-repository-url>


## 3️⃣ Generate the .war Package

Get inside the project directory and generate the package.

**Command**

mvn package


This will generate the build/package for the project.

---

## ⚙️ Tomcat Instance

### 4️⃣ Configure the Tomcat Instance

Connect to the Tomcat instance.

**Configure Security Group**
1. Go to the AWS EC2 Dashboard.
2. Select the Tomcat instance.
3. Go to the Security section.
4. Open the associated Security Group.
5. Add an inbound rule for port: `8080`
6. Save the rule.

### 5️⃣ Download Tomcat

Download Tomcat from the Tomcat website.

1. Go to the Tomcat website.
2. Select the required Tomcat version.
3. Copy the download link.
4. Use the wget command to download it.

**Command**

wget -O tomcat.zip <link-of-tomcat>


### 6️⃣ Extract Tomcat and Install Java 17

Extract the downloaded compressed file using tar or unzip.

Install Java 17 in the Tomcat instance.

**Command**

sudo apt install openjdk-17-jdk -y


After extracting Tomcat:

Tomcat Folder
↓
bin
↓
startup.sh


Go inside the bin directory and start Tomcat.

**Command**

./startup.sh start


## 🌐 Access Tomcat

Once Tomcat has started:

1. Copy the Public IP of the Tomcat instance.
2. Open the browser.
3. Enter the Public IP with port 8080.

http://<tomcat-public-IP>:8080


---

## 🔑 Configure SSH Connection Between Maven and Tomcat

To transfer the .war file from the Maven instance to the Tomcat instance, an SSH connection needs to be established.

### 7️⃣ Generate SSH Key

On the required instance, generate an SSH key.

**Command**

ssh-keygen


### 8️⃣ Find the SSH Public Key

Go inside the hidden files/folders.

**Check hidden files**

ls -a


Go inside the `.ssh` directory:

cd .ssh


View the public key:

cat id_rsa.pub


Copy the public key.

### 9️⃣ Add the Public Key to Tomcat Instance

Go to the Tomcat instance.

Check the hidden files:

ls -a


Go inside the `.ssh` directory:

cd .ssh


Edit the authorized_keys file:

vi authorized_keys


Add the public key copied from the Maven instance.

Save and exit the file.

---

## 🔗 Verify Both Instances are Connected

### 1️⃣ Connect from Maven Instance to Tomcat Instance

Go to the Maven instance and execute:

ssh ubuntu@<tomcat-public-IP>


This will log into the Tomcat instance.

If the connection is successful, the Maven instance can connect to the Tomcat instance.

**To come back to the Maven instance**

exit


---

## 📦 Deploy the .war File from Maven to Tomcat

### 1️⃣ Go to Maven Instance

Go to the Maven instance where the .war file is present.

### 2️⃣ Copy the .war File to Tomcat

Copy the .war file into the Tomcat webapps directory using the scp command.

**Command**

scp ./<path-of-war-file> username@<public-IP-of-tomcat>:/<path-of-webapps>


**Command Breakdown**

./<path-of-war-file>
↓
Source Path

username@<public-IP-of-tomcat>:/<path-of-webapps>
↓
Destination Path


So the flow is:

🛠️ Maven Instance
│
│ scp
│
│ .war file
▼
⚙️ Tomcat Instance
│
▼
webapps/
│
▼
🌐 Application


### 3️⃣ Verify the Deployment

After copying the .war file:

1. Go to the browser.
2. Open the Tomcat Public IP.
3. Use port 8080.
4. Check whether the application has been deployed successfully.

http://<tomcat-public-IP>:8080


---

## 🔄 Complete Tomcat Deployment Workflow
            🛠️ Maven Instance
                   │
                   ▼
            Clone Project
                   │
                   ▼
              mvn package
                   │
                   ▼
                .war
                   │
                   │ SCP
                   ▼
            ⚙️ Tomcat Instance
                   │
                   ▼
              webapps/
                   │
                   ▼
             🌐 Application
                   │
                   ▼
          <Public-IP>:8080

---

## 🧠 Quick Revision
Launch 2 EC2 Instances
↓
Maven Instance
↓
Install Java + Maven
↓
Clone Spring PetClinic Framework
↓
mvn package
↓
Generate .war file
↓
Configure Tomcat Instance
↓
Enable Port 8080
↓
Download Tomcat
↓
Install Java 17
↓
Start Tomcat
↓
Generate SSH Key
↓
Configure authorized_keys
↓
Verify SSH Connection
↓
Copy .war using SCP
↓
Place .war in webapps/
↓
Open Public-IP:8080
↓
Verify Application

---

## 💡 My Takeaway

- Tomcat is a web server where web applications can be deployed.
- A Maven project can be packaged into a .war file.
- The .war file can be transferred from the Maven EC2 instance to the Tomcat EC2 instance using SCP.
- The .war file is placed inside the Tomcat webapps directory for deployment.
- Tomcat can be accessed through port 8080.
- SSH is used to establish the connection between the Maven and Tomcat instances.
