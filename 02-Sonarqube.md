# 🔍 SonarQube

**SonarQube** is an open-source tool that automatically inspects source code to detect **bugs, security issues, and code quality issues**, helping developers write clean, safe, and maintainable code.

**OR**

It is a **source code analyzing tool** used to scan the source code and generate a report in **metrics format**.

---

# 🛠️ To Implement SonarQube

## 1️⃣ Launch EC2 Instances

Launch **2 instances**:

- One instance for **Maven**
- One instance for **SonarQube**

### Instance Configuration

- **Instance Type:** `t2.medium`
- **Operating System:** Ubuntu
- **Storage:** 10–15 GB

```text


              AWS EC2
                 │
        ┌────────┴────────┐
        │                 │
        ▼                 ▼
  🛠️ Maven Instance   🔍 SonarQube Instance
        │                 │
     t2.medium          t2.medium
        │                 │
      Ubuntu            Ubuntu


2️⃣ Install Tools on Maven Instance

Connect to the Maven instance and install the required tools.

Commands
sudo apt update

sudo apt install openjdk-17-jdk -y

sudo apt install maven -y

3️⃣ Clone the Spring PetClinic Framework Repository

Clone the spring-petclinic-framework repository into the Maven instance.

Command
git clone <repository-url>

4️⃣ Generate the Build

Get inside the project directory.

Verify that pom.xml is present.

Then generate the build using:

mvn package

This will generate the project build/package.

🔍 SonarQube Instance Setup

5️⃣ Configure Port 9000

Connect to the SonarQube instance and follow these steps:

Go to the AWS EC2 instance dashboard.
Select the SonarQube instance.
Go to Security.
Click on the Security Group link.
Click on Add Rule.
Enable port number:
9000
Click Save Rules.
📥 Download SonarQube

Download SonarQube from the official website using the wget command.

Command
wget -O sonar.zip <sonarqube-download-url>

6️⃣ Extract SonarQube and Install Java 17

Install unzip and extract the downloaded SonarQube archive.

Commands
sudo apt install unzip

unzip sonar.zip

sudo apt install openjdk-17-jdk -y
📂 Go to the SonarQube Directory

Go inside the SonarQube folder and follow this path:

/bin/linux-x86-64

Then run the sonar.sh script.

Command
./sonar.sh start
🌐 Access SonarQube

Go to the browser and enter:

http://<PUBLIC-IP>:9000

Replace <PUBLIC-IP> with the public IP address of the SonarQube EC2 instance.

🔐 Login to SonarQube

Use the default credentials:

Username: admin
Password: admin

After logging in:

Login using the default credentials.
Change the password according to the requirements specified by SonarQube.

📊 Creating a Project in SonarQube

Follow the steps below to create and analyze a project.


1️⃣ Create a Local Project

Click on:

Create Local Project

2️⃣ Give Project Details

Provide the Project Name.

The Project Key will be generated automatically.


3️⃣ Create the Project

Click on:

Create Project

The project will be created.


4️⃣ Select Local Analysis

To analyze the project:

Select Locally.
Generate a token for the project.
Enter a suitable Token Name.
Select the build tool:
Maven

5️⃣ Copy the Maven Command

SonarQube will display a command for analyzing the project.

Copy the command.

Go to the Maven EC2 instance and paste the command there.


6️⃣ Generate the SonarQube Report

After running the Maven/SonarQube command:

Go back to the SonarQube dashboard.
Open your project.
The analysis report will be generated.

The report contains metrics related to the project's source code.


🔄 SonarQube Workflow
        👨‍💻 Source Code
              │
              ▼
       🛠️ Maven Instance
              │
              ├── Compile
              ├── Test
              └── Build
              │
              ▼
        🔍 SonarQube
              │
              ▼
       🔎 Source Analysis
              │
              ▼
        📊 Metrics Report
              │
       ┌──────┼────────┐
       ▼      ▼        ▼
     🐛 Bugs  🔐 Security  📈 Code Quality



🧠 Quick Revision
1. Launch 2 EC2 instances
       ↓
2. Configure Maven instance
       ↓
3. Clone the project
       ↓
4. Run mvn package
       ↓
5. Configure SonarQube instance
       ↓
6. Enable port 9000
       ↓
7. Download SonarQube
       ↓
8. Install Java 17 & unzip
       ↓
9. Start SonarQube
       ↓
10. Open SonarQube using PUBLIC-IP:9000
       ↓
11. Create Local Project
       ↓
12. Generate Token
       ↓
13. Select Maven
       ↓
14. Run the generated command on Maven instance
       ↓
15. View the SonarQube metrics report


💡 My Takeaway
SonarQube helps analyze source code and provides a metrics-based report containing information about code quality, bugs, and security issues.

In this setup, Maven is used to build the project while SonarQube is used to analyze the source code and generate the report.
