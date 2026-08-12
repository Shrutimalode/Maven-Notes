# 🔨 Build Process & Build Tools

## 🏗️ What is a Build?

- A **Build** is the process of converting the source code into a executable file that can be run on any computer as a package.

**OR**

- It is a compilation process where the source code will be converted into an executable format (`.exe`).

---

## 🔄 Traditional Build Process

Source code is the foundation of an application.

```
Source Code
    │
    ├──→ Compilers
    │
    └──→ Libraries
```

The build process also involves **Build Engineers**.

### 📦 Dependencies

Dependencies are the pre-written set of code that your project needs in order to run the application properly.

**Examples**
- JUnit
- TestNG

### 🔌 Plugins

A plugin is a small software component that adds specific features or functionality to an existing application or system without changing its main code.

**Examples**
- Grammarly
- DarkReader
- AdBlock

### ⚙️ Steps to Build a Package

1. **Validate** → Verifying everything is correct
2. **Compile**
3. **Test**
4. **Package**

### ❌ Drawbacks

- More manual work
- Less efficient
- Time consuming
- Error prone

To overcome these problems, we have **Build Tools**.

---

## 🛠️ Build Tool

A Build Tool is a tool which converts source code into an executable file.

### 🧰 List of Build Tools

1. **ANT** — Open source; used for Java, also supports C/C++, Python
2. **Gradle** — Open source; used for Java, C/C++, Scala; built with Java & Groovy
3. **MS Build** — By Microsoft (C#); mostly for .NET projects
4. **PyBuilder** — Open source; Python only; built with Python
5. **Maven** — Open source; used for Java, Scala, Ruby; built with Java by Apache

---

## 🚀 Maven

Maven is a build automation tool which generates the build automatically.

### 📜 History of Maven

Originally developed by **"Java Van Zyl"** and **Apache Software Foundation**. First released in **2004**.

### ✨ Features of Maven

1. **🆓 Free and Open Source**
2. **📦 Dependency Management** — dependencies auto-downloaded from the Maven official website
3. **📄 pom.xml**
   - POM = Project Object Model
   - XML = Extensible Markup Language

   | HTML | XML |
   |---|---|
   | Used to develop a web application | Used to store project details |
   | Built-in tags | User-defined tags |
   | `<p>`, `<head>`, `<body>` | `<plugins>`, `<dependencies>` |

4. **🔌 Good Plugin Ecosystem**
5. **🔄 Built-in Lifecycle**
6. **📚 Repositories**
7. **👍 Easy to Use**

### 📁 Maven Repositories

1. **💻 Local Repository** — `.m2` folder; caches dependencies/builds locally
2. **🌐 Central Repository** — official Maven site (e.g. TestNG)
3. **☁️ Remote Repository** — stores the build (e.g. Nexus)

### 🔄 Maven Lifecycle

1. **Default Lifecycle** — creates the project, generates the build
2. **Clean Lifecycle** — project cleaning
3. **Site Lifecycle** — project documentation

#### 🔨 Phases of Default Lifecycle

| # | Phase | Description | Command |
|---|---|---|---|
| 1 | Validate | Checks project details | `mvn validate` |
| 2 | Compile | Compiles source code | `mvn compile` |
| 3 | Test | Tests the source code | `mvn test` |
| 4 | Package | Creates `.war`/`.jar` build | `mvn package` |
| 5 | Verify | Verifies the package | `mvn verify` |
| 6 | Install | Installs build locally | `mvn install` |
| 7 | Deploy | Deploys to remote repo (Nexus) | `mvn deploy` |

#### 🧹 Phases of Clean Lifecycle

- Pre-clean → checks prerequisites
- Clean → `mvn clean`
- Post-clean → verifies cleaning

#### 📚 Phases of Site Lifecycle

- Pre-site → checks prerequisites
- Site → `mvn site`
- Post-site → verifies docs generated

---

## ⚙️ Maven Installation

**Requirements:** Maven, Java 17

### ☕ Install Java 17
1. Search "Java 17" in the browser
2. Download and extract the file
3. Install with default steps
4. Verify: `java --version`

### 🛠️ Install Maven
1. Search "Maven for Windows"
2. Click **Installation**
3. Click **"Binary distribution archive"**
4. Click **"binary zip archive"**
5. Extract and configure Maven environment variables

---

## 📦 Generate a Sample .jar Project

1. Create a folder, open VS Code there
2. Run: `mvn archetype:generate`
3. Press Enter for default template
4. Select the latest version
5. Provide `groupId` (company name) and `artifactId` (project name)
6. Verify details, type `y` to confirm
7. Project is created
8. Confirm `pom.xml` exists
9. Run through the Maven Lifecycle commands

---

## 🌐 Generate a Sample .war Project

1. Create a folder, open VS Code there
2. Run: `mvn archetype:generate`
3. Filter web projects: `maven-archetype-webapp`
4. Rename `index.jsp` → `index.html`, save
5. Follow the Maven Lifecycle steps

---

---

## 💡 My Takeaway

- Build is the process of converting source code into a standalone form.
- Build tools help automate the build process and reduce manual work.
- Maven is an open-source build automation tool that automatically generates the build.
- Maven provides dependency management, plugins, repositories and built-in lifecycles.
- `pom.xml` is the Project Object Model file used to store project details.
- Maven has three lifecycles: Default, Clean and Site.
