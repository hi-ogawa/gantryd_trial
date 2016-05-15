### Experiment on Container Deployment with Gantryd (Gantry)

__1__. Server Setup

Install docker and gantryd (gantry) on remote host with ansible:

```
$ ansible -i hosts -l vagrant all -m ping  # ssh connection check
$ ansible-playbook install.yml -i hosts -l vagrant
```

__2__. Build Docker Container

Docker container is built via Webhook from Github to Docker Hub: https://hub.docker.com/r/hiogawa/gantryd_trial/

Or, you can build it manually from local:

```
$ docker build -t hiogawa/gantryd_trial ./node_app
$ docker push hiogawa/gantryd_trial
```

__3__. Deploy Docker Container via gantry

```
$ ansible-playbook deploy.yml -i hosts -l vagrant
```
