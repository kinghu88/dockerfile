## 命令 


```
docker run -d \
--name myvsftpd \
-v /data/ftp-data:/home/vsftpd \
-p 21:21 \
-p 21100-21110:21100-21110 \
-p 20:20 \
-e FTP_USER=your_account \
-e FTP_PASS=your_password \
-e PASV_MIN_PORT=21100 \
-e PASV_MAX_PORT=21110 \
-e PASV_ADDRESS=你的IP \
kinghu88/vsftp:latest
```

```
docker run -d \
--name myvsftpd \
-v /data/ftp-data:/home/vsftpd \
--network host \
-e FTP_USER=your_account \
-e FTP_PASS=your_password \
-e PASV_MIN_PORT=21100 \
-e PASV_MAX_PORT=21110 \
-e PASV_ADDRESS=你的IP \
kinghu88/vsftp:latest
```

添加多个账号，需要进入容器内部进行，然后重启容器
```
docker exec -it myvsftpd /bin/bash
mkdir /home/vsftpd/your_account
echo -e "your_account\your_password" >> /etc/vsftpd/virtual_users.txt
/usr/bin/db_load -T -t hash -f /etc/vsftpd/virtual_users.txt /etc/vsftpd/virtual_users.db
```