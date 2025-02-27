# Jenkin Pipeline -
- Jenkins Pipeline is a suite of plugins that supports implementing and integrating continuous delivery (CD) pipelines into Jenkins.
- It enables you to define your build, test, and deployment process as code using a Jenkinsfile.
- Pipeline as Code: Uses a Jenkinsfile to define the CI/CD process.
- Version Control: Pipelines can be stored in Git for tracking changes.
- Automation: Reduces manual work in building, testing, and deploying applications.
- Integration: Supports multiple tools like Docker, Kubernetes, AWS, and more.
- Parallel Execution: Can run multiple steps simultaneously to speed up execution.

# Types of Jenkins Pipelines 
## 1. Declarative Pipeline -
- Uses a simple and structured format.
- Easier to write, read, and maintain.
- You define what should happen step by step.
- Uses the pipeline {} block.




          pipeline {
              agent any
              stages {
                  stage('Build') {
                      steps {
                          echo 'Building the project...'
                      }
                  }
                  stage('Test') {
                      steps {
                          echo 'Running tests...'
                      }
                  }
                  stage('Deploy') {
                      steps {
                          echo 'Deploying the project...'
                      }
                  }
              }
          }




## 2. Scripted Pipeline -
- Uses the Groovy programming language.
- More flexible and powerful but harder to understand.
- Allows writing dynamic logic inside the pipeline.
- Uses the node {} block.





        node {
            stage('Build') {
                echo 'Building the project...'
            }
            stage('Test') {
                echo 'Running tests...'
            }
            stage('Deploy') {
                echo 'Deploying the project...'
            }
        }








## Difference Between Declarative and Scripted Pipelines in Jenkins

| Feature            | Declarative Pipeline           | Scripted Pipeline               |
|--------------------|--------------------------------|--------------------------------|
| **Definition**     | Uses a simple, structured format. | Uses Groovy programming for full control. |
| **Syntax**        | Uses `pipeline {}` block. | Uses `node {}` block. |
| **Ease of Use**   | Easier to write and understand. | More complex. |
| **Customization** | Limited but enough for most cases. | Full flexibility to customize automation. |
| **Error Handling**| Built-in error handling. | Requires manual error handling. |


