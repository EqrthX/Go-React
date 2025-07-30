# Docker commands
.PHONY: build up down logs clean restart

# Build และรัน containers
build:
	docker-compose build

up:
	docker-compose up -d

# รัน containers แบบดู logs
dev:
	docker-compose up

# หยุด containers
down:
	docker-compose down

# ดู logs
logs:
	docker-compose logs -f

# ดู logs ของ app เท่านั้น
logs-app:
	docker-compose logs -f app

# Restart application
restart:
	docker-compose restart app

# ลบ containers และ volumes
clean:
	docker-compose down -v
	docker system prune -f

# เข้าไปใน app container
shell:
	docker-compose exec app sh

# เข้าไปใน postgres container
db-shell:
	docker-compose exec postgres psql -U myuser -d mydb

# รัน migration (ถ้ามี)
migrate:
	docker-compose exec app go run migrate.go

# ติดตั้ง dependencies
deps:
	go mod tidy
	go mod download

# รัน tests
test:
	docker-compose exec app go test ./...

# Build สำหรับ production
build-prod:
	docker build -t go-react-app:latest .

# รัน development server โดยตรง (ไม่ใช้ docker)
run:
	go run main.go