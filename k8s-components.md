The commonly used k8s components:


Pod
A Pod is an abstraction over one or more containers that share network and storage resources. A Pod is the smallest deployable unit that k8s can manage.
Pods are ephemeral; they can be stopped and restarted at any time. This is referred to as the Pod’s lifecycle. The restart of a Pod will cause the IP assigned to the pod to be different between restarts.

Node
Pods run on a Node. A Node is any machine (virtual or otherwise) that has the necessary k8s components installed (kubelet and a container runtime like Docker) that allow k8s to manage the machine and the pods on the machine.

Service
A Service in k8s is an abstraction that allows us to define a logical set of Pods and a policy to access these Pods. The Service can have a VIP and can designate the Pods that it is going to delegate incoming requests. Pods, and other k8s components, can be assigned labels. We use selectors to match against labels rather than IPs.

Deployments
k8s allows us to define Deployments these are configurations that we can describe in a YAML file and then send to the k8s system through the kubectl command. Deployments defines

Volumes
Pods can have access to resources on the Node they are running including the filesystem. However, much like containers, Pods are ephemeral and thus store state is also ephemeral which makes it an issue when we want to persist data that live beyond the Pod’s lifecycle. Nodes can run more than 1 Pod and there are systems that need to share files.

ConfigMap
k8s allows us to store and share non-confidential data across Pods and services. A ConfigMap allows us to define key-value pairs that are given to k8s and k8s makes these available to components.

Secrets
A very common use case is the need to store and securely recall secrets for our applications. Connecting to a DB, for example, will require our service to be able to use a login and password pair to establish a connection.
k8s provides an Object called Secrets that we can configure and populate with encrypted data.

Ingress
k8s provides Ingress a configuration that we can provide to k8s that specifies incoming public HTTP(S) requests and their internal targeted k8s service. An Ingress Controller is an implementation that we can use to follow our Ingress configuration.