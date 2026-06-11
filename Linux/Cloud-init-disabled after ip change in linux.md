# Ubuntu Netplan and Cloud-Init Network Configuration Guide
### Date: 11-Jun-2026
### Author: Htoo Eain Lin

## 1. Edit Netplan Configuration

```bash
vi /etc/netplan/50-cloud-init.yaml
```

## 2. Generate and Apply Netplan

```bash
sudo netplan generate
sudo netplan apply
```

### Troubleshooting

* Common typo: `gerenate` → use `generate`
* Restart Network Manager if needed:

```bash
sudo systemctl restart Network-Manager
sudo systemctl status Network-Manager
```

## 3. Disable Cloud-Init (Optional)

```bash
cd /etc/cloud/
ls -l
sudo touch cloud-init.disabled
```

## 4. Verify Netplan Configuration

```bash
cat /etc/netplan/50-cloud-init.yaml
sudo netplan generate
sudo netplan apply
```

## 5. Reboot Server

```bash
sudo reboot
```

✅ Steps allow you to update network settings using Netplan and optionally disable Cloud-Init on Ubuntu.
