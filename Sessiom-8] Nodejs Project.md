# On Jenkin Server(8080) -
- Create new item.
- Select Pipelines.
- Ok
- Add Description.
- Select trigger as "GitHub hook trigger for GITScm polling".
- Under Pipeline ---> Inside sceript add your script.


          pipeline {
              agent any
               tools{
                   nodejs 'add your node installation name'
               }
               stages {
                  stage('Git cloning') {
                      steps {
                          echo 'github checkout'
                          checkout scmGit(branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/vishakhadhonde9/Pipelines.git']])
                      }
                  }
                  stage('Build') {
                      steps {
                          echo 'Building Nodejs-app'
                          sh "npm install"
                      }
                  }
                  stage('Test') {
                      steps {
                          echo 'Testing'
                          sh "./node_modules/mocha/bin/_mocha --exit ./test/test.js"
                      }
                  }
                  stage('Deploy'){
                      steps{
                          echo "Deploying"
                          }
                      }
                  }
              }
          }
          


  
- Save.
