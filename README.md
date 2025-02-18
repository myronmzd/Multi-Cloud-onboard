![Build Status](https://img.shields.io/github/actions/workflow/status/username/repository/workflow.yml?branch=main)

# Multi-Cloud-onboard
This is a sample repo for multi cloud onboarding with Python on AWS ,Azure, GCP  

(note whe creating this repo I use .gitignore file for Python is used to tell Git which files and directories to ignore in a Python project. This helps prevent unnecessary files (such as compiled files, virtual environments, or secrets) from being tracked in the repository.)

Steps to follow 

#1 AWS 

As AWS Cloud9 is not working and AWS suggest to use Cloud Shell so lets try it 

Creating a SSH key so that all the Cloud services can connect to github 

 Commad 
 ```bash
ssh-keygen -t rsa 
```
then after clicking 4 times it will generate the key 
then cat the path in which it saves it in cloud shell 
copy the output and add it in your github account settings/SSH_and_GPG_keys New key

in cloud shell to get the repo so that we can edit and test in cloud our code 
```
git clone git@github.com:myronmzd/Multi-Cloud-onboard.git
```

Now the List of thing to do in Cloud with this repor 

1. Create virtualenv
2. Create scaffalting


1. Creating a python enve and write a python program show that we can run this program in any cloud setup
   ```sh
   optional
   mkdir -p ~/venvs
   cd ~/venvs
   
   python3 -m venv ~/.Multi-Cloud-onboard
   source ~/.Multi-Cloud-onboard/bin/activate
   python3 --version
   which python
   ```

   (Multi-Cloud-onboard) Multi-Cloud-onboard $ which python
    ~/Multi-Cloud-onboard/Multi-Cloud-onboard/bin/python
   
3. Create scaffalting
   
   *Makefile
   *hello.py (sourece code)
   *requirements.txt
   *test

   ```sh
   touch Makefile
   touch hello.py
   touch requirements.txt
   touch test_hello.py 
   ```

   Makefile
   ```
    install:
  	pip install --upgrade pip &&\
  		pip install -r requirements.txt

    lint:
      pylint --disable=R,C hello.py
    
    format:
      black *.py
    
    test:
      python -m pytest -vv --cov=hello test_hello.py
    
    deploy:
      echo "CD"
    all: install lint test
   ```

   hello.py

   ```
   def add(x,y):
    return x+y
   print(add(6,6))
   ```
   after runing make install ,make lint , make test ,make deploy 
   then you can use git commit to repo
   and then switch to other clouds and try it there 
