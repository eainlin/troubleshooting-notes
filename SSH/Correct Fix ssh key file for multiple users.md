# SSH Authorized Keys Configuration Guide
### Date: 11-Jun-2026
### Author: Htoo Eain Lin

## 1. Edit SSH Configuration

```bash
sudo nano /etc/ssh/sshd_config
```

## 2. Update AuthorizedKeysFile

Replace all lines related to `AuthorizedKeysFile` with exactly:

```
AuthorizedKeysFile %h/.ssh/authorized_keys
```

* `%h` represents the user’s home directory:

  * `/home/test01/.ssh/authorized_keys` for `test01`
  * `/home/ubuntu/.ssh/authorized_keys` for `ubuntu`

## 3. Restart SSH Service

```bash
sudo systemctl restart ssh
```

## 4. Test SSH Login

```bash
ssh -i test01 test01@103.67.203.22
```

✅ This ensures that SSH keys are correctly recognized for each user in their home directory.
