# Docker

[Docker](https://www.docker.com/) is a platform for developers and sysadmins to develop, deploy, and run applications with containers. The use of Linux containers to deploy applications is called containerization. Containers are not new, but their use for easily deploying applications is.

Installing docker is best done by following the instructions on the [official docker website](https://docs.docker.com/engine/install/ubuntu/). Once that is done, remember to add your user to the docker group:

```bash
sudo usermod -aG docker $USER
```

Next, you will need to restart your computer for the changes to take effect.
