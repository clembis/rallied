# Personal Rally Benchmark

## WIP 

Not usable at this time

### Description

Based on Rally benchmark for Openstack (xrally) : https://github.com/openstack/rally-openstack
Full documentation for Docker based xRally : https://github.com/openstack/rally/tree/master/etc/docker

### Pre-Requisites

```
podman pull xrally/xrally-openstack
podman image list
mkdir -p /opt/rally/reports
sudo chown -R 65500 /opt/rally
podman run -v /opt/rally:/home/rally/.rally --name my-run docker.io/xrally/xrally-openstack db create && podman rm my-run
podman run -v /opt/rally:/home/rally/.rally --name my-run docker.io/xrally/xrally-openstack plugin list --platform openstack && podman rm my-run
```

### Run those scripts 

0. Edit example_env.json with your cloud connections values

1. Edit args/args.yaml with your values (defaults values are present in files however)

2. Start a task based on files presents in subfolders

```
podman run -v /opt/rally:/home/rally/.rally --name my-run docker.io/xrally/xrally-openstack env create --name my_openstack --spec example_env.json && podman rm my-run 
podman run -v /opt/rally:/home/rally/.rally --name my-run docker.io/xrally/xrally-openstack env check && podman rm my-run
podman run -v /opt/rally:/home/rally/.rally --name my-run docker.io/xrally/xrally-openstack task start ./sla_validation/minimal_requirements.yaml --task-args {"image_name": "image_to_use", "flavor_name": "flavor_to_use"} && podman rm my-run
podman run -v /opt/rally:/home/rally/.rally --name my-run docker.io/xrally/xrally-openstack task report --out report.html && podman rm my-run
```

3. You can export existing results 

```
podman run -v /opt/rally:/home/rally/.rally --name my-run docker.io/xrally/xrally-openstack task report <id> --out /home/rally/.rally/reports/report.html
```
