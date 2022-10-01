# internetmonitor_pod

Solution to run an internet monitor in a podman pod

Based on Jeff Geerlings internet monitor

Runs a grafana frontend, with prometheus, blackbox and speedtest containers

## Installation
copy the monitor directory to your desired location. I typically put this in /srv/monitor on my system
Add the nginx snippet to your nginx configuration

Double check the settings in grafana.ini; make sure you have the correct domain name
## To create the pod

```
./create_pod
```

## Generating a systemd configuration

```
podman generate systemd --new --files --name monitor
```

## Deploying to systemd
```
mkdir -p ~/.config/systemd/user
cp *.service ~/.config/systemd/user
systemctl --user daemon-reload
# stop the pod
./pod_stop
# Start the systemd service in user space
systemctl --user start pod-monitor
```



