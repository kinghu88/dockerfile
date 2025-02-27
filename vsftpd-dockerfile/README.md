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