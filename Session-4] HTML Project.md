# Jenkin -
- Create directory: mkdir htmlproject.
- Create file with .html extension.
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

            zip myfile.zip ./*html

- Save.

# On Github -
- Create github repository.
- Add Webhook.


# Jenkin -
- Install Zip.
  
         sudo apt update
         sudo apt install zip
  
- Push files on github.

# Create Production Server-
- Install nginx.
- Install zip.
- Remove index.html file.

  
# On PowerShell -

            scp -i path-to-keypar.pem path-to-keypair.pem ubuntu@ip_of_jenkin:/home/ubuntu/htmlproject(dirname)

- Check with ls command.

# Jenkin Server (8080)
- Again configure project.
- Add execute shell:

            
            chmod 600 keypair.pem
            scp -i keypair.pem -o StrictHostKeyChecking=no myfile.zip ubuntu@ip_of_prodserver:~
            ssh -i keypair.pem -o StrictHostKeyChecking=no ubuntu@ip_of_prodserver<<EOF
            sudo cp myfile.zip /var/www/html
            cd /var/www/html
            sudo unzip myfile.zip
            EOF

















