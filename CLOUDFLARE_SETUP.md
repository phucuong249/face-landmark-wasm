# Hướng dẫn cài đặt Cloudflare Pages

## Phương pháp 1: Cài đặt qua tích hợp GitHub

1. Đăng nhập vào [Cloudflare Dashboard](https://dash.cloudflare.com/)
2. Trong menu bên trái, chọn **Pages**
3. Chọn **Connect to Git**
4. Chọn GitHub làm nhà cung cấp và xác thực với GitHub
5. Chọn repository `face-landmark-wasm`
6. Cấu hình như sau:
   - **Project name**: face-landmark-wasm (hoặc tên bạn muốn)
   - **Production branch**: main
   - **Build settings**:
     - **Framework preset**: None
     - **Build command**: (để trống)
     - **Build output directory**: .
   - **Environment variables**: Không cần thiết lập
7. Chọn **Save and Deploy**

## Phương pháp 2: Sử dụng GitHub Actions

1. Trong GitHub repository của bạn, tạo secrets sau:
   - `CLOUDFLARE_API_TOKEN`: API token của Cloudflare với quyền Pages:Write
   - `CLOUDFLARE_ACCOUNT_ID`: ID tài khoản Cloudflare của bạn

2. Để tạo API token:
   - Đăng nhập vào [Cloudflare Dashboard](https://dash.cloudflare.com/)
   - Vào **My Profile** > **API Tokens** > **Create Token**
   - Chọn template "Edit Cloudflare Workers"
   - Ở phần Account Resources, chọn "Include - All accounts" và "All zones"
   - Ở phần Permissions, thêm "Pages - Edit"
   - Tạo token và lưu giá trị

3. Để lấy Account ID:
   - Đăng nhập vào [Cloudflare Dashboard](https://dash.cloudflare.com/)
   - Account ID nằm ở góc phải bên dưới

4. Push code lên GitHub sẽ tự động kích hoạt workflow triển khai

## Xác nhận cài đặt

Sau khi triển khai, kiểm tra header bằng cách:

```bash
curl -I https://your-project.pages.dev
```

Bạn sẽ thấy header `Cross-Origin-Opener-Policy: same-origin` và `Cross-Origin-Embedder-Policy: require-corp` trong phản hồi. 