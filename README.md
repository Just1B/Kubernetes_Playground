# Gcloud Workflow with Kubernetes

[![forthebadge](https://forthebadge.com/images/badges/made-with-go.svg)](https://forthebadge.com)

This Repo describe a deployment process on Google Cloud

Requirements
- Google Cloud SDK
- A Cluster Already Online
- A Project in Cloud Console

# Submit your container to Google Container Registry

    gcloud container builds submit --tag gcr.io/{PROJECT_ID}/go-example:1.0 .

When it's done, you will see your image [here](https://console.cloud.google.com/gcr) 

# Edit the Deployment file

    image: gcr.io/{PROJECT_ID}/go-example:1.0

# Running in the Cluster

First we will setup a `loadbalancer` service to expose an IP

    kubectl create -f service.yaml

Next Watch until we get an `EXTERNAL-IP`

    kubectl get svc -w

Deploy our Application

    kubectl create -f deployement.yaml

![index](https://github.com/Just1B/Kubernetes_Playground/raw/master/screen/screen.png)

# Test our App

Navigate on `EXTERNAL-IP`/justin to get some love 😍😍😍😍😍😍

# Clear the Stack 

    kubectl delete deployment go-example
    kubectl delete service go-example

The MIT License

Copyright (c) 2018 JUST1B

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
