# Postman API Tests với GitHub Actions CI/CD

Dự án này sử dụng GitHub Actions để tự động chạy Postman tests trong quá trình CI/CD.

## Cấu trúc dự án

```
├── .github/workflows/
│   └── postman-ci.yml             # Workflow tổng hợp cho CI/CD
├── data/
│   ├── post_favorite_test_data.csv
│   ├── get_favorite_test_data.csv
│   └── delete_favorite_test_data.csv
├── Favorite API Tests - Data Driven.postman_collection.json
└── Favorite API Environment.postman_environment.json
```

## Workflow

### Postman CI/CD (postman-ci.yml)
- **Trigger**: Push/PR vào main/develop + Manual trigger
- **Jobs**:
  - **Basic Tests**: Chạy toàn bộ collection tests
  - **Data-Driven Tests**: Chạy tests với CSV data (post/get/delete)
- **Reports**: CLI output + JUnit XML cho từng job

## Cách sử dụng

### Tự động chạy
1. Push code lên branch `main` hoặc `develop`
2. Tạo Pull Request
3. Workflow sẽ tự động chạy

### Chạy thủ công
1. Vào GitHub Actions tab
2. Chọn workflow "Postman API Tests CI/CD"
3. Click "Run workflow"
4. Chọn loại test muốn chạy:
   - **all**: Chạy cả basic và data-driven tests
   - **basic**: Chỉ chạy tests cơ bản
   - **data-driven**: Chỉ chạy data-driven tests

### Xem kết quả
- **GitHub Actions**: Xem logs và status
- **Artifacts**: Download test results XML
- **Test Results**: Xem chi tiết trong PR/commit

## Cấu hình

### Environment Variables
Thêm vào GitHub repository secrets:
```
API_BASE_URL=https://your-api-url.com
API_KEY=your-api-key
```

### Newman Options
- `--bail`: Dừng khi có test fail
- `--reporters cli,junit`: Xuất reports
- `--iteration-data`: Sử dụng CSV data

## Troubleshooting

### Lỗi thường gặp
1. **File không tìm thấy**: Kiểm tra tên file collection/environment
2. **Data CSV lỗi**: Kiểm tra format CSV
3. **API timeout**: Tăng timeout trong Newman

### Debug
- Xem logs trong GitHub Actions
- Download artifacts để phân tích
- Chạy locally với Newman CLI

## Dependencies

- Node.js 18+
- Newman CLI
- GitHub Actions runners (ubuntu-latest) 