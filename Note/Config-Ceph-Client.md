# 1. Tải và cài đặt key cho Ceph client

## 1.1. Tạo thư mục chứa data

```Ruby
mkdir -p /storage/media
mkdir -p /storage/deepface
```

## 1.2. Tải về Ceph key và tiến hành add key

`wget -q -O- 'https://download.ceph.com/keys/release.asc' | sudo apt-key add - && \`

## 1.3. Add repository theo hệ điều hành và cài đặt Ceph-common

`wget -q -O- 'https://download.ceph.com/keys/release.asc' | sudo apt-key add - && sudo apt-add-repository 'deb https://download.ceph.com/debian-pacific/ focal main' && apt update && sudo apt-get install ceph-common -y`

## 1.4. Tạo và phân quyền thực thi thư mục chứa Ceph

`mkdir -p -m 755 /etc/ceph`

## 1.5. Khởi tạo cấu hình Ceph tối thiểu thông qua Ceph Cluster daemon và lưu trữ nội dung cấu hình vào ceph.conf

`ssh root@10.10.10.125 "sudo ceph config generate-minimal-conf" | sudo tee /etc/ceph/ceph.conf`

# 2. KEYRING SETUP

## 2.1. Để tạo tệp khóa có thông tin xác thực cho client.fs, hãy đăng nhập vào một cluster member đang chạy và chạy lệnh sau

`ceph auth get-or-create client.fs`

## 2.2. Kết quả đầu ra được chuyển trực tiếp vào một tệp keyring, thường là

`/etc/ceph/ceph.keyring`

## 2.3. Tạo hoặc Kiểm tra key của Ceph Client

`vi /etc/ceph/ceph.client.deepface.keyring`

## 2.4. Mount phân vùng media từ Ceph server về ceph client

`mount -t ceph :/pvc-volumes/test-media /storage/media -o name=deepface,fs=fs_halo`

## 2.5. Phân quyền cho ceph client key

`chmod 600 /etc/ceph/ceph.client.deepface.keyring`

## 2.6. Chỉnh sửa filesystem fstab chứa thông tin phân vùng

`vi /etc/fstab`

```shell
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during curtin installation
/dev/disk/by-uuid/173d5231-38a1-43ac-b796-cf772432c9df / ext4 defaults 0 0
:/pvc-volumes/test-media /storage/media ceph name=deepface,fs=fs_halo,noatime,_netdev 0 2
:/volumes/sb-hahaloloGroup/sb_hahalolo_deepface/4b7990cd-df06-4663-9ebc-baad5140ecbd /storage/deepface ceph name=sb_hahalolo_deepface,>
```

## 2.7. Mount tất cả filesystem được đề cập trong fstab

`mount -a`

## 2.8. Kiểm tra disk space

`df -h`

## 2.9. Tạo subkey file, phân quyền và mount tất cả nội dung trong file fstab

```shell
cd /etc/ceph/
vi ceph.client.sb_hahalolo_deepface.keyring
chmod 600 /etc/ceph/ceph.client.sb_hahalolo_deepface.keyring 
mount -a
df -h
```

## 2.10. Tạo thử tập tin tại thư mục vừa mount

```shell
cd /storage/media/
touch 1
```
