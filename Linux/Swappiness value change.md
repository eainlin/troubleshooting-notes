# Linux Swappiness and Swap Management Guide
### Date: 11-Jun-2026
### Author: Htoo Eain Lin
## Swappiness Values

* Range: **0 to 100**
* **0** → Avoid swapping, keep data in RAM
* **100** → Swap aggressively
* **Default** → 60 (balanced, may be aggressive for servers)

### Check Current Value

```bash
cat /proc/sys/vm/swappiness
```

### Set Temporary Value

```bash
sudo sysctl -w vm.swappiness=10
```

### Set Permanent Value

```bash
echo "vm.swappiness=10" | sudo tee -a /etc/sysctl.conf
sudo sysctl -p
```

### Recommended Values

* Desktop/Laptop: 60 (default) or 30 (SSD)
* Database Servers: 1–10 (keep DB in RAM)
* Low-memory servers: 60+

### Check Swap Usage

```bash
swapon --show
```

## Swap File Management

### Step 1: Turn off current swap

```bash
sudo swapoff /swap.img
```

### Step 2: Resize Swap File

**Option A: Delete and Recreate**

```bash
sudo rm /swap.img
sudo fallocate -l 4G /swap.img   # create 4GB swap file
sudo chmod 600 /swap.img
sudo mkswap /swap.img
```

**Option B: Resize with dd**

```bash
sudo dd if=/dev/zero of=/swap.img bs=1M count=4096
sudo chmod 600 /swap.img
sudo mkswap /swap.img
```

### Step 3: Enable Swap

```bash
sudo swapon /swap.img
```

### Step 4: Make Permanent

Add to `/etc/fstab`:

```
/swap.img none swap sw 0 0
```

### Step 5: Verify

```bash
swapon --show
free -h
```

You should see:

```
NAME      TYPE SIZE USED PRIO
/swap.img file 4G   0B   -2
```
