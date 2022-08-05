# Config đường dẫn mới cho application

## Add route gateway

Clone source config-file về `https://gitlab.hahalolo.com/microservice/core-config-files`

Thêm route gateway vào config-file

```yaml
routes:
    - id: ~<service-name>~
            uri: lb://~<service-name>~
            predicates:
                - Path=/~<path-name>~/**
            filters:
                - RewritePath=/aut/(?<path>.*), /$\{path}
```