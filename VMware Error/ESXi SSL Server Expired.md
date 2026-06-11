# ESXi SSL Certificate Renewal Guide

## 1. Connect to ESXi Host via SSH

```bash
ssh root@your-esxi-host
```

## 2. Backup Existing SSL Certificates

```bash
cd /etc/vmware/ssl
mv rui.crt rui.crt.old
mv rui.key rui.key.old
```

## 3. Generate New Certificates

```bash
/sbin/generate-certificates
```

## 4. Restart ESXi Services

```bash
/etc/init.d/hostd restart
/etc/init.d/vpxa restart
```

## 5. Optional: Reboot Host

```bash
reboot
```

✅ This process replaces the default SSL certificates with new ones and restarts necessary ESXi services.
