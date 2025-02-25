
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


# 1] Build -
#3 Jenkin Server -
- Create directory nodeapp
- Install and setup Git.
- Create two files package.json and index.js as above.

## Connect to Jenkins- (8080)
- Create new item.
- Add Description.
- Select Source Code Management as git and add git repo link.
- Select trigger as "GitHub hook trigger for GITScm polling"
- Save.



### To add node env.-
- Go to Dashboard.
- Select Manage Jenkins.
- Select Plugins.
- Available Plugins.
- Sesrch nodejs plugin and install with same version as deployment server.
- Restart Jenkin.
- Connect To jenkin again.

### Go to your project and configure again-
- Add env as provide node and npm
- Add Build Step: execute shell -----> npm install.


# On github -
- Create webhook:
        add payload as "http://ip_of_jenkinserver:8080/github-webhook/


# On Jenkin Server -
- Push files on github.


# 2] Test -
- Create dir test.
- Create file test.js.



                    var request = require('supertest');
                    var app = require('../index.js');
                    
                    describe('GET /', function () {
                      after(function () {
                        process.exit(0); // Ensure Mocha exits after tests
                      });
                    
                      it('respond with 404 page not found', function (done) {
                        request(app)
                          .get('/nonexistentpage')
                          .expect(404, done);
                      });
                    });
                    



- Add file into workspace.

## Connect To Jenkins(8080)
- Add New item.
- Add Description.
- Select Source Code Management as git and add git repo link.
- Select trigger as "Build after other Project".
          - Add watch as "buildprojetname.
          - Build if first is stable.
-  Add env as provide node and npm
- Add Build Step: execute shell -----> npm install.   ./node_modules/mocha/bin/_mocha --exit ./test/test.js
- Save.

## On server -
- Push files on github.

# 3] Production Server/Deploy -
## On Jenkin Server (8080)-
- Go to Dashboard ----> Manage Jenkins ----> Plugin ----> Available Plugins ----> Search (SSH) ----> Install ----> Restart.
- Go to Dashboard ----> Manage Jenkins ----> Security ----> Credentials ----> Global ----> Add Credentials ----> SSH Username with Private Key ----> Username(ubuntu) and private key(.pem).
- Go to Dashboard ----> Manage Jenkins ----> System ----> SSH Remote host -----> username, hostIP (ip of deployement server), port(22), key (.pem).


- Add New item.
- Add Description.
- Select Source Code Management as git and add git repo link.
- Select trigger as "Build after other Project".
          - Add watch as "testprojetname.
          - Build if first is stable.
-  Add env as provide node and npm
- Add Build Step: execute shell


       cd /home/ubuntu/node1
       git pull repolink
       npm install
       npm run
       sudo npm install -g pm2
       pm2 start index.js

  
- Save.















