Pod lifecycle and Pod states
✅ Troubleshooting Pods
✅ Kubelet troubleshooting
✅ Master Node vs Worker Node communication issues
✅ Horizontal Pod Autoscaler (HPA) vs Cluster Autoscaler
✅ Node autoscaling concepts
✅ Internal Load Balancer vs External Load Balancer vs DNS flow

🌐 Kubernetes Advanced

✅ Service Mesh (Istio)
✅ ELK Stack (Elasticsearch, Logstash, Kibana)
✅ Granting Pods access to GCS buckets (Workload Identity/Service Accounts)


=========
What happens internally when you run `docker run`?
2. Difference between CMD and ENTRYPOINT.
3. Why is a pod stuck in CrashLoopBackOff? How would you debug it?
4. Difference between Deployment, StatefulSet, DaemonSet, and Job.
5. Readiness Probe vs Liveness Probe.
6. Kubernetes pods are running but users receive 503 errors. What will you check?
7. How does Kubernetes Service Discovery work?
8. Explain ConfigMaps and Secrets. How do you manage them across environments?
========================

An application's expected latency is 1 second, but in production it's taking 5 seconds. What could be the possible root causes, and how would you troubleshoot and resolve the issue?
🔹 Kubernetes Troubleshooting
What is a CrashLoopBackOff, and what steps would you follow to resolve it?
🔹 Observability
How would you integrate Prometheus and Grafana with a Kubernetes cluster?
🔹 Incident Response
You receive a Prometheus alert stating "NODE_0 ERROR". What are your immediate next steps, and how would you identify and fix the issue?
🔹 Kubernetes Workloads
What are the key differences between a Deployment, StatefulSet, and DaemonSet?
🔹 Kubernetes Operations
What is the purpose of the kubectl rollout command, and when is it commonly used?
🔹 Kubernetes Architecture
What is etcd? If it crashes or is accidentally deleted, what impact does it have on the Kubernetes cluster?
==================

3. How would you schedule a pod on a specific node group in Kubernetes?
Expected discussion:
✅ Node Labels
✅ Node Selectors
✅ Taints and Tolerations
✅ Node Affinity
4. What are Affinity and Anti-Affinity Rules?
Expected discussion:
✅ Node Affinity
✅ Pod Affinity
✅ Pod Anti-Affinity
✅ preferredDuringSchedulingIgnoredDuringExecution
✅ requiredDuringSchedulingIgnoredDuringExecution
5. How would you troubleshoot a pod stuck in Pending state?
Expected discussion:
✅ kubectl describe pod
✅ Resource constraints
✅ Node availability
✅ Taints and tolerations
✅ PVC issues
✅ Scheduler events
6. How would you design a CI/CD pipeline for a Kubernetes application?
Expected discussion:
✅ GitHub → Jenkins
✅ Docker build
✅ Image scanning
✅ Push to registry
✅ Helm deployment
✅ Rollback strategy
7. Difference between Horizontal Pod Autoscaler (HPA) and Cluster Autoscaler?
Expected discussion:
✅ HPA scales pods
✅ Cluster Autoscaler scales nodes
✅ Metrics Server integration
✅ Resource optimization


============

They want to know:
🔹 How you troubleshoot production issues
🔹 How you design systems
🔹 How you automate repetitive tasks
🔹 How you handle real-world Kubernetes and CI/CD challenges

===========

Explain the complete request flow from a browser to a Kubernetes Pod.
What happens internally when you run a Docker container?
How does Kubernetes decide which node should run a Pod?
What is the difference between Readiness, Liveness, and Startup Probes?
Why can a Pod be in the Running state while the application is still unavailable?
Why is a Pod stuck in CrashLoopBackOff?
How do you troubleshoot CrashLoopBackOff?
What is the difference between Deployment, StatefulSet, DaemonSet, and Job?
How would you schedule a Pod on a specific node group?
What are Node Labels, Node Selectors, Taints/Tolerations, and Node Affinity?
What are Affinity and Anti-Affinity rules?
How would you troubleshoot a Pod stuck in Pending state?
What are the worker-node components?
What is imagePullPolicy?
What happens when a Pod becomes unhealthy?
How does Kubernetes recover an unhealthy Pod?
How do you ensure zero-downtime deployments?
Explain rolling updates and rollbacks.
What is the difference between Pod, Deployment, ReplicaSet, StatefulSet, and DaemonSet?
What is the difference between ClusterIP, NodePort, and LoadBalancer?
What are Taints and Tolerations?
What is kube-proxy?
What are the different types of Kubernetes Services?
What is a Headless Service and how does it work?
What is a NodePort Service?
How do you restart a Kubernetes Deployment?
How do you perform an application health check?
Which probe acts first — Startup, Readiness, or Liveness?
How would you move workloads from an unhealthy node to a healthy node in production?
What is the difference between Taint and Cordon?
What is HPA and how is it different from Cluster Autoscaler?
How do you troubleshoot Kubernetes networking?
How do you handle uneven traffic distribution across Pods?
What happens when Pods are running but the application returns HTTP 503?
How do you perform an EKS/AKS upgrade?
How do you troubleshoot Master/Control Plane and Worker Node communication issues?



=================

3. How do you configure sticky sessions in Kubernetes?
4. What is the difference between StatefulSet and Deployment?
5. How do PersistentVolumes (PV) and PersistentVolumeClaims (PVC) work?
6. What happens internally when you apply a StatefulSet YAML?
7. Let's say in Kubernetes users has reported latency related issues while accessing the application how will you fix this issue give me ans in layer wise approach.



===========================













