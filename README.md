# EMS Infrastructure

Repo này quản lý **hạ tầng toàn bộ hệ thống ESM microservices**:

- **esm-gateway**: API Gateway
- **esm-auth**: Authentication Service
- **esm-core**: Core Service (quản lý transaction)
- **esm-report**: Report / Analytics Service
- **Databases**: MySQL cho auth & core
- **Message Queue**: RabbitMQ

---

## **Yêu cầu**

- Docker >= 20
- Docker Compose >= 1.29

---

## **Cấu trúc repo**

```
esm-infra/
├─ docker-compose.yml       # Compose file chạy full system
├─ README.md
└─ .gitignore
```

- Các service code nằm trong các repo riêng:
  - ../esm-gateway
  - ../esm-auth
  - ../esm-core
  - ../esm-report

---

## **Cách chạy full system**

1. Clone infra repo:

```bash
git clone https://github.com/yourusername/esm-infra.git
cd esm-infra
```

2. Chạy toàn bộ service bằng 1 lệnh:

```bash
docker-compose up
```

- Docker sẽ **build image từ Dockerfile của từng service**  
- Chạy container cho:
  - `esm-gateway` → http://localhost:3000
  - `esm-auth` → http://localhost:3001
  - `esm-core` → http://localhost:3002
  - `esm-report` → http://localhost:3003
  - RabbitMQ Web UI → http://localhost:15672 (user/password: guest)
  - MySQL auth → port 3307
  - MySQL core → port 3308

---

## **Chạy ở background**

```bash
docker-compose up -d
```

- Thêm `-d` để chạy detached mode

---

## **Xem logs**

```bash
docker-compose logs -f gateway
docker-compose logs -f auth
docker-compose logs -f core
docker-compose logs -f report
```

---

## **Dừng hệ thống**

```bash
docker-compose down
```

- Dừng và xóa tất cả container
- Dữ liệu MySQL vẫn còn nếu dùng volume (hiện tại đang dùng default container storage)

---

## **Portfolio tip**

- Clone repo infra → `docker-compose up` → chạy full EMS system **ngay lập tức**  
- HR / Tech Lead có thể kiểm tra nhanh toàn bộ microservice architecture

