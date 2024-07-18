FROM mysql:latest

# Sử dụng microdnf để cài đặt các gói bổ sung
RUN microdnf update && microdnf install -y \
    vim \
    && microdnf clean all

# Tùy chỉnh cấu hình MySQL nếu cần
COPY my.cnf /etc/mysql/my.cnf

# Thiết lập biến môi trường
ENV MYSQL_DATABASE=mydb
ENV MYSQL_USER=myuser
ENV MYSQL_PASSWORD=mypassword
ENV MYSQL_ROOT_PASSWORD=rootpassword

# Mở cổng 3306
EXPOSE 3306

# Chạy MySQL
CMD ["mysqld"]
