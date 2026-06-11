# Proxmox VM Removal Guide When Storage is Missing
### Date: 11-Jun-2026
### Author: Htoo Eain Lin

## Issue

When trying to destroy a VM:

```bash
qm destroy 114
```

You may see:

```
storage 'LightNodeSMBShare' does not exist
```

## Steps to Resolve

### 1. Edit VM Configuration

```bash
nano /etc/pve/qemu-server/114.conf
```

### 2. Remove Missing Disk References

* Look for lines like:

```
scsi0: LightNodeSMBShare:114/vm-114-disk-0.qcow2
```

* Delete any lines referencing the missing storage.

### 3. Destroy the VM Again

```bash
qm destroy 114
```

* This should now work because the disk entries are removed.

### 4. Verify VM Status

```bash
qm status
```

* Ensure the VM is no longer listed.
