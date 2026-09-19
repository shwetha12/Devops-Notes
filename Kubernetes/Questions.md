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









