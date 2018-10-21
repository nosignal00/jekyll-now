---
layout: post
title: jupyter on ec2 설정방법 
---
Create a password for jupyter notebook
ipython

from IPython.lib import passwd

passwd()

Enter password: [Create password and press enter] Verify password: [Press enter]

'sha1:98ff0e580111:12798c72623a6eecd54b51c006b1050f0ac1a62d'

exit

Create config profile
jupyter notebook --generate-config

Create certificates for https
mkdir certs

cd certs

sudo openssl req -x509 -nodes -days 365 -newkey rsa:1024 -keyout mycert.pem -out mycert.pem

Answer questions

Configure jupyter
cd ~/.jupyter/

vi jupyter_notebook_config.py

c = get_config()

# Kernel config
c.IPKernelApp.pylab = 'inline'  # if you want plotting support always in your notebook

# Notebook config
c.NotebookApp.certfile = u'/home/ubuntu/certs/mycert.pem' #location of your certificate file
c.NotebookApp.ip = '*'
c.NotebookApp.open_browser = False  #so that the ipython notebook does not opens up a browser by default
c.NotebookApp.password = u'sha1:'  #the encrypted password we generated above
# Set the port to 8888, the port we set up in the AWS EC2 set-up
c.NotebookApp.port = 8888
