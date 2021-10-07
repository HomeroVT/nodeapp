# A simple web server
A simple web server in nodejs. It is intended for demo only, no production. A Dockerfile is provided in the reposistory to build a docker image and run the application as linux container.

On CentOS linux, install and start Docker

    [ec2-user@ip-private ~]$ sudo yum install -y docker
    [ec2-user@ip-private ~]$ sudo service docker status

Install git and clone the reposistory

    [ec2-user@ip-private ~]$ sudo yum install -y git
    [ec2-user@ip-private ~]$ git clone https://github.com/HomeroVT/nodeapp.git
    [ec2-user@ip-private ~]$ cd nodeapp

Build a Docker image

    [ec2-user@ip-private  nodeapp]$ docker build -t nodeapp .
    [ec2-user@ip-private  nodeapp]$ docker images
    REPOSITORY            TAG                 IMAGE ID            CREATED             SIZE
    nodejs-web-app        latest              e6e0578f5f2d        2 minutes ago       659.6 MB

Start the container by setting the desired answer message in the MESSAGE env variable

    [ec2-user@ip-private ~]$ docker run --name=web -p 80:8080 -d -e MESSAGE="Thanks for all the fish ..." nodejs-web-app
    [ec2-user@ip-private ~]$ curl localhost:80
    Thanks for all the fish ...
