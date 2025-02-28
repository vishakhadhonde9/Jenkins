# Jenkin -
- Create directory: mkdir pythonproject.
- Create file inside pythonproject.
    - Dockerfile
    - App.py
    - requirement.txt

#### App.py -

      from flask import Flask
      
      app = Flask(__name__)
      
      @app.route('/')
      def home():
          return "Hello from Flask App running in Docker!"
      
      if __name__ == '__main__':
          app.run(host='0.0.0.0', port=5000)


#### Requirement.txt -

    flask

#### Dockerfile -


        FROM python:3.8-slim
        
        # Set the working directory
        
        WORKDIR /app
        
        # Copy the requirements file and install dependencies
        
        COPY . /app
        
        RUN pip install --no-cache-dir -r requirements.txt
        
        # Expose the port the app runs on
        
        EXPOSE 5000
        
        ENV NAME World
        
        # Set the command to run the application
        
        CMD ["python", "app.py"]



 
- Install Python and Flask env.

        sudo apt update
        sudo apt install python3 python3-pip -y
        pip3 install flask
    

- Initialize and configure git.

      git remote add origin
      git add .
      git commit -m "cm1"


# Jenkin Server (8080)-
- Create new item.
- Add Description.
- Select Source Code Management as git and add git repo link.
- Select trigger as "GitHub hook trigger for GITScm polling"
- Select Build Step as "Execute Shell".

            sudo docker build -t flask-img .
            sudo docker stop flask-container || true
            sudo docker rm flask-container || true
            sudo docker run -d -p 80:5000 --name flask-container flask-img


- Save.

# On Github -
- Create github repository.
- Add Webhook.
- Push files on github.

