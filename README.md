# Personal Rally Benchmark

## WIP 

Not usable at this time

### Description

Based on Rally benchmark for Openstack : https://github.com/openstack/rally-openstack

### Run those scripts 

0. Edit example_env.json with your cloud connections values

1. Edit args/args.yaml with your values (defaults values are present in files however)

2. Start a task based on files presents in subfolders

```
rally task start sla_validation/minimal_requirements.yaml --task-args-file ./args/args.yaml
```

3. Once your task has ended, you can output results 

```
rally task report <id> --out report.html
```
