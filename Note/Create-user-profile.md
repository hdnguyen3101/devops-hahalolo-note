# Tạo profile server cho user

Tạo các file .properties cho các mỗi user tương ứng cho từng project khác nhau. VD: hfeed-duy.properties (lấy properties mẫu tại server 10.10.11.51/10.10.11.52)
Nội dung các file properties cần lưu ý: server.port, spring.application.name, spring.application.description. VD:

```ini
server.port=9098
spring.application.name=fheed-duy
spring.application.description=core-rest-social-hotel
```

Mỗi khi project được build sẽ check file bootstrap.yml (hoặc application.properties đối với dự án local) để chạy.
File bootstrap định nghĩa thông tin các profile, URL để đọc file properties từ server 10.10.11.51/10.10.11.52, thông tin config để lưu Username/password dùng để xác thực khi đọc properties từ server.
[VD:]

```yaml
config:
      username: ${CONFIG_USERNAME}
      password: ${CONFIG_PASSWORD}
```

```yaml
spring:
  application:
    name: hfeed-duy, consul-local, feign-local, oauth2-resource-local
  profiles:
    - duy
  cloud:
    config:
      uri:
        - http://test-config-server-1.hahalolo.com
        - http://test-config-server-2.hahalolo.com
```

Thông tin config sẽ được cấu hình trong spring boot java như hình
![image](20220505101811.png)  
