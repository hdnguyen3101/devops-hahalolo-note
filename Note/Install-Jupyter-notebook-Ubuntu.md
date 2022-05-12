# Install Jupyter notebook on Ubuntu 20.04

## Install pip3

`sudo apt install python3-pip python3-div`

Nếu đã cài pip3 thì dùng lệnh upgrade pip : `sudo -H pip3 install --upgrade pip`
![command](../Image/2022-05-12-10-23-08.png)

## Create virtual environment

`sudo -H pip3 install virtualenv`

![command](../Image/2022-05-12-10-24-53.png)

## Create thư mục cho virtualenv

`mkdir jupyter`

## Create Python virtual-environment, tên 'environment'

`virtualenv environment`

![command](../Image/2022-05-12-10-29-19.png)

## First load virtual-environment before install Jupyter

### Use path 'bin/activate' to active environment

`source environment/bin/activate`

![command](../Image/2022-05-12-10-32-26.png)

## Download Jupyter in a virtual-environment

`pip install jupyter`

![run pip in virtual-environment](../Image/2022-05-12-10-36-52.png)

## Run Jupyter

`jupyter notebook` thêm optional --allow-root nếu đang chạy user root

![--allow-root](../Image/2022-05-12-10-39-20.png)

Output sẽ có cảnh bảo `No web browser found: could not locate runnable browser.` do server hoạt động no GUI, nhưng ko ảnh hưởng đến kết quả. Tiếp tục sử dụng SSH Tunel để kết nối tới Jupyter Notebook

# Connecting to the Jupyter Notebook Application with SSH Tunneling

# For End-user

## Use Powershell on Windows to connect SSH

Mở Terminal hoặc Powershell trên Windows, sử dụng lệnh SSH với optional -L để chỉ định một cổng nhất định trên host sẽ được chuyển tiếp đến máy chủ và cổng trên remote server.
Điều này có nghĩa là bất kỳ nội dung nào đang chạy trên cổng được chỉ định trên remote server (8888, cổng mặc định của Jupyter Notebook) sẽ xuất hiện trên cổng được chỉ định trên host (ví dụ cổng 8000).

`ssh -L 8000:localhost:8888 root@10.10.15.87`

![Connect SSH Tunel](../Image/2022-05-12-11-25-55.png)

Di chuyển tới thư mục Jupyter
`cd ../jupyter/`

![jupyter](../Image/2022-05-12-13-20-37.png)

## After connect SSH, active virtual-environment and run Jupyter

Dùng lệnh `source environment/bin/activate` để kích hoạt environment. Và chạy Jupyter notebook với optional --allow-root.

```text
jupyter notebook --allow-root
```

![Run jupter notebook by ssh](../Image/2022-05-12-11-29-52.png)

## Use Browser connect to Jupyter Notebook

Trên máy host nhập đường dẫn vào trình duyệt để dùng Jupter Notebook.
`http://localhost:8000/`

![Jupyter](../Image/2022-05-12-11-32-47.png)

Nhập token:

Token auto generate khi chạy Jupyter notebook.
![token](../Image/2022-05-12-13-24-56.png)
