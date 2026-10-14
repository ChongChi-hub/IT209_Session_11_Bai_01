# Báo cáo Thực hành DevOps - Session 11: Bài 1

## Khởi tạo Workflow chạy Unit Test tự động cho Java Spring Boot với Gradle

### 1. Giới thiệu tổng quan
Bài thực hành này triển khai luồng tích hợp liên tục (Continuous Integration - CI) tự động trên GitHub Actions cho dự án Java Spring Boot quản lý bởi Gradle. Mục tiêu chính là thiết lập runner Ubuntu, cài đặt môi trường Java JDK 17 (phân phối Temurin), cấp quyền thực thi cho Gradle Wrapper và tự động kích hoạt kiểm thử JUnit mỗi khi có thay đổi được đẩy (push) lên nhánh `main`.

### 2. Cấu trúc thư mục bài nộp
```text
SS11_HW01_DaoTrongTri_PTIT062/
├── .github/
│   └── workflows/
│       └── ci.yml             # Tệp kịch bản GitHub Actions Workflow
├── gradle/
│   └── wrapper/
│       ├── gradle-wrapper.jar
│       └── gradle-wrapper.properties
├── src/
│   ├── main/
│   │   ├── java/com/ptit/devops_ss11/Application.java
│   │   └── resources/application.properties
│   └── test/
│       └── java/com/ptit/devops_ss11/ApplicationTests.java
├── .gitignore
├── build.gradle
├── gradlew
├── gradlew.bat
├── settings.gradle
├── README.md                  # Hướng dẫn và tổng quan bài tập
└── REPORT.md                  # Báo cáo kỹ thuật chi tiết kèm log và minh chứng
```

### 3. Tóm tắt nội dung kịch bản CI (`.github/workflows/ci.yml`)
- **Tên Workflow:** `Java Spring Boot CI (Gradle)`
- **Sự kiện kích hoạt (`on`):** Sự kiện `push` lên nhánh `main`.
- **Môi trường chạy (`runs-on`):** `ubuntu-latest`.
- **Các bước (`steps`):**
  1. `actions/checkout@v5`: Kéo mã nguồn dự án về không gian làm việc của Runner.
  2. `actions/setup-java@v5`: Cài đặt môi trường Eclipse Temurin OpenJDK 17.
  3. `chmod +x gradlew`: Cấp quyền thực thi (`execute`) cho tập lệnh Gradle Wrapper.
  4. `./gradlew test`: Khởi chạy toàn bộ các bài kiểm thử JUnit.

Chi tiết báo cáo và hướng dẫn xác nhận kết quả kiểm thử trên GitHub Actions vui lòng xem tại [REPORT.md](REPORT.md).
