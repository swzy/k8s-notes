## General

K8s provides a toolkit providing:
- Container replication
- Load balancing
- Autoscaling
- Self-healing deployments

## K8s components
- kubelet
  - Daemon that monitors state of all the pods running on the node. It continually compares the current state to the desired state. Communicates with <u>apiserver</u> in the control plane.
- kube-proxy
  - Network proxy using OS-native packet filtering software.
- kube-apiserver
  - Public REST api for the K8s cluster.
- etcd
  - Persistent data storage for app that holds app state, config details, and secrets.
- kube-scheduler
  - Assess which pods run on which nodes based on:
    - hardware/software compatibility
    - data locality
    - schedule deadlines
  - Assigns new or unassociated pods to the right nodes.
- kube-controller-manager
  - Manages control loops to ensure container self-healing
  - Compares the current state of the cluster to the desired state and will try to solve differences.

## K8s Deployment
<u>Control Plane</u> and any associated pods and nodes comprise a K8s cluster. It can be created, modified, and configured, and scaled directly from the console via kubectl CLI.

Dynamic scaling can be determined from deployment details.

## Services
With pods that are constantly shifting, a <u>Service</u> provides a consistent access interface for a set of related pods.

## Example commands
Create a deployment:

`kubectl create deployment demo-app --image=nginx`

Scale to three containers:

`kubectl scale deployment demo-app --replicas=3`

Set autoscaling based on CPU threshold of 80%:

`kubectl autoscale deployment demo-app --cpu-percent=80 --min=1 --max=5`

Delete deployment resources:

`kubectl delete deployment demo-app`

Query list of pods:

`kubectl get pods --selector app=demo-app`

Define and deploy a service based on a yaml file:

`kubectl apply -f demo-service.yaml`