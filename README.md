# RabbitMQ Cluster on OpenShift/Kubernetes

This is an opinionated [OpenShift](https://www.openshift.com/) template for a [RabbitMQ](https://www.rabbitmq.com/) cluster using [StatefulSets](https://kubernetes.io/docs/concepts/workloads/controllers/statefulset/). The cluster members are auto discovered using the [Kubernetes peer discovery](http://www.rabbitmq.com/cluster-formation.html#peer-discovery-k8s) plugin.

The following resources are created with this template:
* StatefulSet with 3 replicas (creates PVCs for each replica)
* Secret with default username/password and erlang cookie (generated)
* RoleBinding (view role to default service account)
* ConfigMap with keys containing
    * `enabled_plugins` file content
    * `additional_erl_args` containing additional erlang VM arguments
* Service mapping ports 15672/TCP, 5672/TCP, 25672/TCP, 4369/TCP

#### Additional Configuration
Additional configurations can be passed in by editing the `additional_erl_args` value. This is expected in the erlang configuration format.

#### Template Installation
```sh
oc create -f openshift-template.yml
```

