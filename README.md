[![Python application test with GitHub Actions](https://github.com/myronmzd/Multi-Cloud-onboard/actions/workflows/main.yml/badge.svg)](https://github.com/myronmzd/Multi-Cloud-onboard/actions/workflows/main.yml)

# Multi-Cloud Onboarding

This repository provides a sample setup for multi-cloud onboarding using Python across AWS, Azure, and GCP.

## Table of Contents
- [Overview](#overview)
- [Prerequisites](#prerequisites)
- [Setup Instructions](#setup-instructions)
  - [1. AWS Cloud Shell](#1-aws-cloud-shell)
  - [2. Virtual Environment Setup](#2-virtual-environment-setup)
  - [3. Project Scaffolding](#3-project-scaffolding)
- [Makefile Commands](#makefile-commands)
- [Running the Code](#running-the-code)
- [Deploying to Other Clouds](#deploying-to-other-clouds)

---

## Overview
This project demonstrates how to set up a simple Python application in a multi-cloud environment. It includes:
- Creating an SSH key for GitHub access.
- Setting up a Python virtual environment.
- Basic project scaffolding with a `Makefile`.
- Running linting and tests.

> **Note:** When creating this repository, a `.gitignore` file was added for Python. This ensures that unnecessary files (such as compiled files, virtual environments, or secrets) are not tracked in Git.

## Prerequisites
- GitHub account with SSH key access.
- AWS Cloud Shell (preferred over AWS Cloud9).
- Python 3 installed.
- Basic knowledge of Git and Python.

## Setup Instructions

### 1. AWS Cloud Shell
AWS suggests using **Cloud Shell** instead of Cloud9. We will set up SSH authentication and clone the repository.

#### Generate an SSH Key
Run the following command in AWS Cloud Shell:
```bash
ssh-keygen -t rsa
```
Press **Enter** four times to accept the default settings. Then, retrieve the generated key:
```bash
cat ~/.ssh/id_rsa.pub
```
Copy the output and add it to your GitHub account under:
**Settings > SSH and GPG Keys > New Key**.

#### Clone the Repository
After adding the SSH key, clone this repository:
```bash
git clone git@github.com:username/Multi-Cloud-onboard.git
cd Multi-Cloud-onboard
```

### 2. Virtual Environment Setup
To create a Python virtual environment:
```bash
# (Optional) Create a directory for virtual environments
mkdir -p ~/venvs
cd ~/venvs

# Create and activate the virtual environment
python3 -m venv ~/.Multi-Cloud-onboard
source ~/.Multi-Cloud-onboard/bin/activate

# Verify Python version and path
python3 --version
which python
```
Expected output:
```bash
(Multi-Cloud-onboard) $ which python
~/Multi-Cloud-onboard/Multi-Cloud-onboard/bin/python
```

### 3. Project Scaffolding
Create necessary project files:
```bash
touch Makefile hello.py requirements.txt test_hello.py
```

#### `Makefile`
```makefile
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

#### `hello.py`
```python
def add(x, y):
    return x + y

print(add(6, 6))
```

---

## Makefile Commands
Run the following commands to set up and test the project:
```bash
make install   # Install dependencies
make lint      # Run linting
make test      # Run tests
make deploy    # Simulate deployment
```

## Running the Code
After running `make install`, `make lint`, and `make test`, you can commit your changes and push them to GitHub:
```bash
git add .
git commit -m "Initial setup for multi-cloud onboarding"
git push origin main
```

## Deploying to Other Clouds
Once the setup is complete on AWS, switch to Azure or GCP and repeat the process using their respective Cloud Shells.

---

This project ensures a seamless onboarding process for multi-cloud environments. Happy coding! 🚀

