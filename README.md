# Deploy-Keptn-Using-K8s
The Keptn project began as a way to assist enterprises in adopting cloud-native strategies for either cutting-edge microservice applications or long-standing monoliths. This ecosystem has been evolving since its inception, focusing on robust continuous delivery with automated testing, quality gates, and auto-remediation capabilities. It now has over 50.

## Pre-Requisites:
Kubctl with atleast one node should be present. OR Minikube should be installed.

## Workings steps to Deploy Keptn with Replication Controller:

- Deploy keptn rs with (default 3 replicas) following command.
```
kubectl create -f keptn-rs.yaml
```

- Get output of running pods using this command.
```
kubectl get po -o wide
```

- Scale Up / Scale Down the pods using this command.
```
kubectl scale rs keptn-rs --replicas=5
kubectl scale rs keptn-rs --replicas=1
```

- Delete keptn-rc after deployment
```
kubectl delete -f keptn-rs.yaml
```
**Note** Also there is a file main.sh that does all the above steps for you :relaxed:

## Executions steps
Just execute the main.sh file using this command. Rest script will handle everything :relaxed:

```
bash main.sh
```

## Flow of Deployment:
```mermaid
flowchart TD
    A[main.sh executed!!];
    A --> B[Enter Number of pods to create for Keptn];
    B --> C[Enter Count];
    C --> D[Keptn deployed];
    D --> E{Do you want to scale up Pods?};
    E -- Yes --> F[Enter number of pods to scale up];
    F --> G[Pods have been scaled up!]
    E -- No --> H{Do you want to scaldown Pods?};
    G --> H{Do you want to scaldown Pods?};
    H -- Yes --> I[Enter number of pods to scale down to];
    I --> J[Pods have been scaled down!];
    H -- No --> K{Do you want to delete this Deployment?};
    J --> K{Do you want to delete this Deployment?};
    K -- Yes --> L[Deployment Deleted!];
    K -- No --> Z[Script Ended Without Deleting Deployment!];
```

## Screenshots of Deployment
- Screenshot for Scale Up deployment
![alt text](./images/Techhub2.png)

- Screenshot for Scale Down deployment
![alt text](./images/techhub2.1.png)