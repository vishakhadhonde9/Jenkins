## Deploy Production Server - 
- Add port 3000 to SG.
- Install Nodejs and npm.

          apt-get install nodejs
          apt-get install npm



- Create pakage.json and index.js file as code given above:
  
#### Package.json -


                    {
                        "name": "node-app",
                        "description": "hello jenkins test app",
                        "version": "0.0.1",
                        "private": true,
                        "dependencies": {
                           "express": "3.12.0"
                        },
                        "devDependencies": {
                           "mocha": "10.2.0",
                           "supertest": "6.3.3"
                        }
                       } 





#### Index.js -

                    var express = require('express');
                     
                    var app = express();//Respond with "hello world" for requests that hit our root "/"
                    app.get('/', function (req, res) {
                     res.send('changed not ');
                    });//listen to port 3000 by default
                    app.listen(process.env.PORT || 3000);
                     
                    module.exports = app;
                     

- npm install
- npm install -g pm2
- pm2 start index.js


# Jenkin Server -
- Create directory nodeapp
- Install and setup Git.
- Create two files package.json and index.js as above.





# On Jenkin Server(8080) -
### Install NodeJs-

- Go to Dashboard.
- Select Manage Jenkins.
- Select Plugins.
- Available Plugins.
- Sesrch nodejs plugin and install with same version as deployment server.
- Restart Jenkin.
- Connect To jenkin again.
- *If already install:  Manage Jenkins ---> Tool ---> NodeJs Installation ---> Name.

### Create Project -
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



















