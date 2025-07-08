# Jenkins Interview Questions and Answers (DevOps Focused)

This README covers simple and practical Jenkins interview questions and answers with real-time examples and syntax. Suitable for DevOps interviews and GitHub documentation.

---

## 📌 1. What is Jenkins?

**Answer:** Jenkins is an open-source CI/CD tool used to automate software development processes such as build, test, and deploy.

**Example:** When you push code to GitHub, Jenkins can automatically build and deploy your app to a server.

---

## 📌 2. What are Jenkins Pipelines?

**Answer:** A Jenkins Pipeline is a series of steps written as code (in `Jenkinsfile`) to automate your CI/CD workflows.

**Why Used:** Makes builds repeatable, version-controlled, and visible.

**Example Jenkinsfile:**

```groovy
pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        echo 'Building the application'
      }
    }
  }
}
```

---

## 📌 3. What is Declarative Pipeline?

**Answer:** A structured format of writing pipelines using `pipeline {}` syntax. Easier to read and maintain.

**Example:**

```groovy
pipeline {
  agent any
  stages {
    stage('Test') {
      steps {
        echo 'Running tests...'
      }
    }
  }
}
```

---

## 📌 4. What is Scripted Pipeline?

**Answer:** Uses full Groovy syntax and offers more flexibility. Written inside `node {}` block.

**Example:**

```groovy
node {
  stage('Build') {
    echo 'Building application...'
  }
}
```

---

## 📌 5. What is SCM in Jenkins?

**Answer:** Source Code Management (e.g., Git). Jenkins pulls code from Git repositories for building/testing.

**Declarative SCM Example:**

```groovy
pipeline {
  agent any
  stages {
    stage('Checkout') {
      steps {
        git 'https://github.com/user/repo.git'
      }
    }
  }
}
```

---

## 📌 6. What are Jenkins Plugins?

**Answer:** Plugins add functionality to Jenkins.

| Plugin        | Purpose                         |
| ------------- | ------------------------------- |
| Git Plugin    | Pull code from Git repositories |
| Maven Plugin  | Build Java projects             |
| Docker Plugin | Manage Docker containers        |
| Slack Plugin  | Send Slack notifications        |
| Blue Ocean    | Modern UI for Jenkins pipelines |

---

## 📌 7. Why Jenkins in DevOps?

**Answer:** Jenkins automates repetitive CI/CD tasks. It integrates easily with Git, Docker, AWS, Kubernetes, etc.

**Example:** Developer commits code ➔ Jenkins runs tests ➔ If successful, deploys to staging server.

---

## 📌 8. Jenkins Master-Slave Architecture

**Master:** Controls job scheduling, provides UI.

**Slave (Agent):** Executes jobs on remote machines.

**Use Case:** Run different jobs on different OS (e.g., Windows build agent, Linux testing agent).

---

## 📌 9. Common Jenkins Pipeline Steps

1. Checkout Code (Git)
2. Build Code (e.g., Maven, Gradle)
3. Run Tests (JUnit, PyTest)
4. Deploy (e.g., to Tomcat, AWS, Docker)
5. Notify (e.g., via Email, Slack)

---

## 📌 10. Jenkins Environment Variables

```groovy
pipeline {
  agent any
  environment {
    VERSION = '1.0.0'
  }
  stages {
    stage('Print') {
      steps {
        echo "App Version is ${VERSION}"
      }
    }
  }
}
```

---

## 📌 11. Jenkins with Maven (Real-time Example)

```groovy
pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'mvn -f myapp/pom.xml clean package'
      }
    }
  }
}
```

---

## 📌 12. How to Trigger Jenkins Jobs?

* Manual Trigger (click "Build Now")
* SCM Webhook (e.g., GitHub push)
* Scheduled (CRON syntax)
* Another Job (Post-build action)

---

## 📌 13. Jenkins Notifications Example (Slack)

Install Slack Plugin and use post section:

```groovy
pipeline {
  agent any
  stages {
    stage('Deploy') {
      steps {
        echo 'Deploying...'
      }
    }
  }
  post {
    success {
      slackSend channel: '#deployments', message: 'Deployment successful!'
    }
  }
}
```

---

## 📌 14. How to Use Credentials in Jenkins

Use `credentialsId` in your steps:

```groovy
withCredentials([usernamePassword(credentialsId: 'git-creds', passwordVariable: 'PASS', usernameVariable: 'USER')]) {
  sh 'git clone https://${USER}:${PASS}@github.com/user/repo.git'
}
```

---

## 📌 15. Difference Between Freestyle and Pipeline Jobs

| Freestyle Job      | Pipeline Job               |
| ------------------ | -------------------------- |
| GUI-based          | Code-based (`Jenkinsfile`) |
| Less Flexible      | More Flexible              |
| No version control | Stored in Git              |

---

## 📌 16. Jenkinsfile in Real Projects

Keep the `Jenkinsfile` in the root of your Git repo.

**Benefits:**

* Pipeline as Code
* Version controlled
* Easier collaboration

---

## 📌 17. Sample Multi-Stage Pipeline (Build, Test, Deploy)

```groovy
pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'mvn clean compile'
      }
    }
    stage('Test') {
      steps {
        sh 'mvn test'
      }
    }
    stage('Deploy') {
      steps {
        echo 'Deploying application...'
      }
    }
  }
}
```

---

## 📌 18. Common Jenkins Interview Tips:

* Know basic pipeline syntax
* Be ready to explain real project pipelines
* Understand plugin usage (Git, Maven, Docker, etc.)
* Explain CI/CD flow clearly
* Practice writing Jenkinsfiles

---

## ✅ Final Tip:

**Use Jenkinsfile + Git + Docker + AWS/K8s for complete real-time DevOps experience.**

---

**Author:** *DevOps Learner*

Feel free to fork and update with more questions or project examples!
