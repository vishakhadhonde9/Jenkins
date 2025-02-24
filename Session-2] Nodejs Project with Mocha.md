# 
## Deploy Production Server -
- Install Nodejs and npm.

          apt-get install nodejs
          apt-get install npm



  
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
mkdir nodeapp












