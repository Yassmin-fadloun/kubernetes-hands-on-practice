# NFS Volume Mount with Sidecar Logging

## Objective

Configure an NFS server and mount a shared volume in a Kubernetes pod using two containers:
- A main container (`nginx`) that serves content from the NFS mount.
- A sidecar container (`busybox`) that logs data into the same volume.

---

## Steps and Commands

### 1. Update the package index
```bash
sudo apt update

