# Bài 2: Khởi chạy Web Server Nginx với Port Mapping

## 1. Mục tiêu

- Khởi chạy Nginx Web Server bằng Docker Container.
- Sử dụng image `nginx:alpine`.
- Chạy container ở chế độ nền với tùy chọn `-d`.
- Ánh xạ cổng `8080` của máy tính tới cổng `80` của container.
- Kiểm tra phản hồi HTTP bằng lệnh `curl`.
- Dừng và xóa container sau khi thử nghiệm.

## 2. Khởi chạy container

Sử dụng lệnh sau để tạo và khởi chạy container:

```bash
docker run -d -p 8080:80 --name my-web nginx:alpine
```

Giải thích:

- `docker run`: Tạo và khởi chạy container.
- `-d`: Chạy container ở chế độ nền.
- `-p 8080:80`: Ánh xạ cổng 8080 trên máy tính tới cổng 80 trong container.
- `--name my-web`: Đặt tên container là `my-web`.
- `nginx:alpine`: Sử dụng image Nginx phiên bản Alpine có dung lượng nhẹ.

## 3. Kiểm tra container

Sử dụng lệnh:

```bash
docker ps
```

Kiểm tra container `my-web` đang chạy và cổng được ánh xạ là `0.0.0.0:8080->80/tcp` hoặc tương đương.

## 4. Kiểm tra Web Server

Gửi HTTP request tới Nginx bằng lệnh:

```bash
curl http://localhost:8080
```

Kết quả mong đợi:

Lệnh `curl` trả về mã HTML của trang mặc định Nginx, trong đó có dòng chữ:

```html
<h1>Welcome to nginx!</h1>
```

Điều này chứng minh Web Server Nginx đã hoạt động và có thể truy cập thông qua cổng 8080 của máy tính.

## 5. Dừng và xóa container

Sau khi kiểm tra xong, chạy lệnh:

```bash
docker stop my-web && docker rm my-web
```

- `docker stop my-web`: Dừng container.
- `docker rm my-web`: Xóa container đã dừng.

Có thể kiểm tra lại bằng lệnh:

```bash
docker ps -a
```

Container `my-web` sẽ không còn xuất hiện trong danh sách.

## 6. Kết luận

Đã thực hiện khởi chạy Nginx Web Server bằng Docker với image `nginx:alpine`, ánh xạ cổng `8080:80`, kiểm tra phản hồi HTTP bằng `curl` và dọn dẹp container sau khi hoàn thành thử nghiệm.
