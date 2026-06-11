# Docker MySQL User Management Guide

## 1. Login to Database Container

```bash
sudo docker exec -it [database_container_id_or_name] sh
mysql -u root -p
```

## 2. Connect to NPM Database

```sql
USE npm;
```

## 3. Mark User as Deleted

```sql
UPDATE user SET is_deleted=1;
```

## 4. Restart Container (Optional)

```bash
sudo docker restart [npm_container_id_or_name]
```

## 5. Restore User

```bash
sudo docker exec -it [database_container_id_or_name] sh
mysql -u root -p
USE npm;
UPDATE user SET is_deleted=0;
```

## 6. Login Credentials

```
Login: admin@example.com
Password: changeme
```
