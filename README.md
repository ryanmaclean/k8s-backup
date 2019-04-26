# k8s-backup
Kubernetes backup solution by exporting all k8s-components into YAML files, archived and encrypted with a password.

- The following K8s components/objects are extracted:
  - Secrets
  - Config Maps
  - Deployments
  - Services
  - Ingress
  - Persistent Volumes
  - Cronjobs

## Usage
```
docker run -it \
-e CLUSTER_NAME=my-cluster-name \
-e KUBE_ARCHIVE_PW=my-secret-password \
-v path-to-kube-config-dir:/root/.kube \
k8s-backup:latest
```

To decrypt the backup/archive run `openssl enc -aes-256-cbc -d -in name.tar.gz.enc | tar xz`.
