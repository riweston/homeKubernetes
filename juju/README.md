# README

## Overview

This folder contains all deployment configuration used by juju to deploy a new cluster

## Deployment

```shell
# (Optional) This is effectively a logical container for the deployment
$ juju add-model home

# Deploy cluster froom the deployment manifest
$ juju deploy ./deployment.yml
```
