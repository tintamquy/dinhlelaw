# Hướng Dẫn Đẩy Code Lên GitHub

## Vấn Đề
Git chưa được cài đặt trên hệ thống của bạn.

## Giải Pháp: Cài Đặt Git

### Bước 1: Tải Git
Truy cập: https://git-scm.com/download/win
Hoặc tải trực tiếp: https://github.com/git-for-windows/git/releases/latest

### Bước 2: Cài Đặt Git
1. Chạy file `Git-2.x.x-64-bit.exe` vừa tải
2. Chọn "Next" cho các tùy chọn mặc định
3. Quan trọng: Chọn "Git from the command line and also from 3rd-party software"
4. Hoàn tất cài đặt và khởi động lại Terminal/PowerShell

### Bước 3: Kiểm Tra Cài Đặt
```powershell
git --version
```

## Các Lệnh Push Code Lên GitHub

Sau khi cài Git, chạy các lệnh sau trong thư mục `c:\projects\dinhle-law`:

```powershell
# 1. Khởi tạo Git repository
git init

# 2. Cấu hình thông tin của bạn (thay YOUR_NAME và YOUR_EMAIL)
git config user.name "Tên của bạn"
git config user.email "email@example.com"

# 3. Thêm tất cả files
git add .

# 4. Commit với message
git commit -m "Initial commit - DINHLE LAW FIRM landing page"

# 5. Đổi nhánh thành main
git branch -M main

# 6. Thêm remote repository
git remote add origin https://github.com/tintamquy/dinhlelaw.git

# 7. Push code lên GitHub
git push -u origin main
```

## Lưu Ý Quan Trọng

### Nếu Repository Đã Tồn Tại
Nếu repository https://github.com/tintamquy/dinhlelaw.git đã có code, bạn có thể cần force push:

```powershell
git push -u origin main --force
```

⚠️ **CẢNH BÁO**: `--force` sẽ ghi đè toàn bộ code cũ trên GitHub!

### Xác Thực GitHub
Khi push lần đầu, GitHub sẽ yêu cầu xác thực:
- **Username**: tên tài khoản GitHub của bạn
- **Password**: Sử dụng Personal Access Token (không phải mật khẩu)

#### Tạo Personal Access Token:
1. Vào GitHub.com → Settings → Developer settings
2. Personal access tokens → Tokens (classic) → Generate new token
3. Chọn quyền: `repo` (full control of private repositories)
4. Copy token và dùng làm password khi push

## Phương Án Thay Thế (Không Cần Git)

### Option 1: GitHub Desktop
1. Tải GitHub Desktop: https://desktop.github.com/
2. Đăng nhập tài khoản GitHub
3. File → Add Local Repository → chọn `c:\projects\dinhle-law`
4. Commit và push qua giao diện

### Option 2: Upload Thủ Công
1. Vào https://github.com/tintamquy/dinhlelaw
2. Click "Add file" → "Upload files"
3. Kéo thả các files: `index.html`, `style.css`, `script.js`, `logo.png`
4. Commit changes

## Files Trong Project

```
c:\projects\dinhle-law\
├── index.html    ✅ Main landing page
├── style.css     ✅ All styles & design system
├── script.js     ✅ Interactive features
└── logo.png      ✅ Company logo
```

## Kiểm Tra Kết Quả

Sau khi push thành công, truy cập:
- Repository: https://github.com/tintamquy/dinhlelaw
- GitHub Pages (nếu đã enable): https://tintamquy.github.io/dinhlelaw/

## Bật GitHub Pages

Để website hiển thị online:
1. Vào repository → Settings → Pages
2. Source: chọn "main" branch
3. Folder: / (root)
4. Save
5. Đợi vài phút, website sẽ live tại: https://tintamquy.github.io/dinhlelaw/

---

**Cần hỗ trợ?** Hãy cho tôi biết bước nào bạn gặp khó khăn!
