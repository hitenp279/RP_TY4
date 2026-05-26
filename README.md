EXP 2

mkdir exp2
cd exp2
git init
code .

exp2content.txt
    Hello DevOps

git status
git add .
git config --global user.name "Hiten Patel"
git config --global user.email "yourmail@gmail.com"
git commit -m "first commit"
git log


EXP 3

mkdir exp3
cd exp3
git init
code .

file.txt
    Hello Exp3

git add .
git commit -m "first commit"
git remote add origin https://github.com/USERNAME/exp3.git
git branch -M main
git push -u origin main


EXP 4

mkdir exp4
cd exp4
git init
nano exp4content.txt

exp4content.txt
    Hello DevOps

git add .
git commit -m "first commit"

git checkout -b hiten

nano exp4content.txt

exp4content.txt
    maybe i am not

git add .
git commit -m "branch hiten"

git checkout master

nano exp4content.txt

exp4content.txt
    master is cooking

git add .
git commit -m "master update"

git merge hiten

nano exp4content.txt

exp4content.txt (resolve conflict)
    master is cooking
    maybe i am not

git add .
git commit -m "merge resolved"
git log


EXP 5

mkdir exp5
cd exp5
git init
code .

.github/workflows/ci.yml

    name: initial

    on: [push]

    jobs:
      build:
        runs-on: ubuntu-latest

        steps:
          - uses: actions/checkout@v4

          - name: Set up Python
            uses: actions/setup-python@v5
            with:
              python-version: "3.11"

          - name: Success Message
            run: echo "Workflow executed successfully"

test.py

    print("Hello DevOps")

git add .
git commit -m "workflow added"
git remote add origin https://github.com/USERNAME/exp5.git
git branch -M main
git push -u origin main


EXP 6

mkdir exp6
cd exp6
git init
code .

.github/workflows/cicd.yml

    name: Python CI/CD Pipeline

    on:
      push:
        branches: [ "main" ]

    jobs:
      build-and-test:
        runs-on: ubuntu-latest

        steps:
          - name: Checkout code
            uses: actions/checkout@v4

          - name: Setup Python
            uses: actions/setup-python@v5
            with:
              python-version: "3.11"

          - name: Install dependencies
            run: |
              python -m pip install --upgrade pip
              pip install -r requirements.txt

          - name: Run test
            run: python test.py

requirements.txt

    pytest

test.py

    print("Hello DevOps")

git add .
git commit -m "CI/CD pipeline added"
git remote add origin https://github.com/USERNAME/exp6.git
git branch -M main
git push -u origin main


EXP 7

mkdir exp7
cd exp7
git init
code .

.github/workflows/test.yml

    name: Testing Workflow

    on:
      push:
        branches: [ "main" ]

    jobs:
      test:
        runs-on: ubuntu-latest

        steps:
          - uses: actions/checkout@v4

          - name: Setup Python
            uses: actions/setup-python@v5
            with:
              python-version: "3.11"

          - name: Install dependencies
            run: |
              pip install -r requirements.txt

          - name: Run tests
            run: pytest

requirements.txt

    pytest

test_sample.py

    def test_add():
        assert 2 + 2 == 4

git add .
git commit -m "automated testing added"
git remote add origin https://github.com/USERNAME/exp7.git
git branch -M main
git push -u origin main


EXP 8

sudo apt install docker.io -y
sudo systemctl start docker
sudo usermod -aG docker $USER
newgrp docker

mkdir exp8
cd exp8
code .

app.py

    print("Hello Docker")

Dockerfile

    FROM python:3.11-slim

    WORKDIR /app

    COPY . .

    CMD ["python", "app.py"]

docker build -t myapp .
docker images
docker run myapp
docker ps -a


EXP 9

mkdir exp9
cd exp9
code .

docker-compose.yml

    version: '3'

    services:
      web:
        image: nginx
        ports:
          - "8080:80"

      db:
        image: mysql
        environment:
          MYSQL_ROOT_PASSWORD: root

docker compose up
docker ps
docker compose down


EXP 10

sudo apt update
sudo apt install ansible -y

mkdir exp10
cd exp10
code .

install.yml

    ---
    - name: Install nginx
      hosts: localhost
      become: yes

      tasks:
        - name: Install nginx
          apt:
            name: nginx
            state: present

        - name: Start nginx
          service:
            name: nginx
            state: started

ansible-playbook install.yml
systemctl status nginx


EXP 11

mkdir exp11
cd exp11
git init
code .

.github/workflows/cicd.yml

    name: End-to-End CI/CD

    on:
      push:
        branches: [ "main" ]

    jobs:
      test:
        runs-on: ubuntu-latest

        steps:
          - uses: actions/checkout@v4

          - name: Setup Python
            uses: actions/setup-python@v5
            with:
              python-version: "3.11"

          - name: Install dependencies
            run: pip install -r requirements.txt

          - name: Run test
            run: python test.py

      deploy:
        needs: test
        runs-on: ubuntu-latest

        steps:
          - name: Deploy
            run: echo "Deployment completed successfully"

requirements.txt

    pytest

test.py

    print("Deployment successful")

git add .
git commit -m "end to end pipeline"
git remote add origin https://github.com/USERNAME/exp11.git
git branch -M main
git push -u origin main
