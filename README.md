# Prometheus & Grafana Exercise #1

## Setup Docker

First, ensure you are using an up-to-date docker engine.

In the terminal,

1. Run `docker info` and check for any errors
1. Run `docker --version` and ensure you have version >=17.06

Ensure you have set enough resources for Docker to run smoothly:
In the taskbar, click the whale icon → Preferences → Advanced

(I set 6 CPUs and 8GB RAM for Docker)

![](./img/docker_engine_settings.png)


## Install Tutorial

1. Run in terminal:
```sh
git clone git@github.com:shelleg/prom_exercise_01.git
cd prom_exercise_01

```

2. choose 1 from 2 option :

```sh
docker-compose up -d

# OR,

docker stack deploy -c docker-compose.yml mon
```

## Browse Prometheus
1. Open your browser :  http://localhost:9090 
2. click Status → Targets : Here we can see that Prometheus can only reach 2 out of the 4 targets we told it to poll.)
3. click Graph  :→ see a long list of metrics in the drop-down. 
4. click execute : These metrics are coming from the container named "node exporter" which produces OS-level metrics for Prometheus to poll.
![](./img/prometheus_targets_before.png)

 
## Browse Grafana
Open your browser : http://0.0.0.0:3000/
login with admin admin



![](./img/prometheus_graphs.png)

## Exercise

1. Add the cAdvisor exporter from https://github.com/google/cadvisor
1. Add a MySQL container to docker-compose.yml
1. Add a MySQL exporter for Prometheus

## Expected Solution

You should have a docker-compose.yml file that includes:

- Prometheus
- Node Exporter
- Grafana
- cAdvisor
- MySQL
- MySQL Exporter

All targets in http://localhost:9090/targets should be **UP** and **green**.

## Docker Tips
2 ui tools for docker:
- docker-visualizer
- portainer


At any point, you can always remove all containers and start over.
Depending if you're using Swarm Mode or not, to REMOVE the stack, run:

For Native Docker:
```sh
docker-compose stop
docker-compose rm -f
```

For Docker Swarm:
```sh
docker stack rm mon
```

### How to Find if You're Using Swarm Mode

```
docker info | grep -i swarm
```
