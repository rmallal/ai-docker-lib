#
# NOTE:
# PLEASE MAKE SURE TO HAVE A GOOGLE CREDENTIALS FILE.
# THIS CREDENTIALS FILE IS SECURITY FILE ENABLING ACCESS
# TO GOOGLE CLOUD SERVICES.
#
# By default Dockerfile expects file 'GCloud_Auth.json' in the 
# current directory.
# You can give Google credentials file any name as long as you 
# edit Dockerfile in the current directory and 
# change reference from 'GCloud_Auth.json' to 'myfile.json'
# 

# Dockerfile SERVES DUAL-PURPOSE

# PURPOSE #1: On-Prem Instance that Access GCloud Services

> docker build --tag="quantumgears/ai-dev:quanta-dynamic-gc-engine" --file Dockerfile .
> docker images # grab the image id 
> docker run -v /var/run/docker.sock:/var/run/docker.sock -it <image-id>


#
# PURPOSE #2: GCloud App Engine Instance Accessing GCloud Services
# Please make sure app.yaml file is in the current directory.
# Firs set the project id
#
> gcloud config set project mygcp-demo
> gcloud app deploy



