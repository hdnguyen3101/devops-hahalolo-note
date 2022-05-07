# 1. Cần tạo service cho chạy jar

## 1.1. Tạo 1 file trong /etc/systemd/system/tên_module.service , ví dụ core-rest-user-syst.service với nội dung sau

```PowerShell
[Unit]
Description=CORE-REST-USER-SYST

[Service]
User=root
WorkingDirectory=/storage/core-rest-user-syst
#executable is a bash script which calls jar file
ExecStart=/storage/core-rest-user-syst/core-rest-user-syst

SuccessExitStatus=143
TimeoutStopSec=10
Restart=on-failure
RestartSec=5

[Install]
WantedBy=multi-user.target
```

## 1.2. Tạo file chạy jar tương ứng với tên trong phần ExecStart của 1.1 với nội dung sau

```Ruby
#!/bin/sh
sudo java -jar -Dspring.profiles.active=testlive core-rest-user-syst-1.0.0-RELEASE.jar
```

## 1.3. Khởi tạo và đăng ký service

```Shell
chmod a+x /storage/core-rest-user-syst/core-rest-user-syst
systemctl daemon-reload
systemctl enable core-rest-user-syst.service
```

## 1.4. Set giá trị environment cho security load config

`nano /etc/enviroment` thêm vào 2 dòng sau

```bash
#Config Server Authentication
CONFIG_USERNAME="config"
CONFIG_PASSWORD="HQwJ86RUxVbdCg9jfZ3X"
```

Sau đó gọi lệnh `source /etc/environment`
Cách test xem source ăn chưa: gọi lệnh`echo $CONFIG_USERNAME`, nếu print ra giá trị là ok
