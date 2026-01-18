# Push Code Lên GitHub - Hướng Dẫn Nhanh

## Vấn Đề: Git Đã Cài Nhưng Chưa Trong PATH

Git đã được cài đặt nhưng PowerShell chưa nhận diện được. Có 2 cách giải quyết:

### Cách 1: Khởi động lại PowerShell (Khuyến nghị)

1. **Đóng hoàn toàn PowerShell/Terminal hiện tại**
2. **Mở lại PowerShell mới**
3. **Kiểm tra:**
   ```powershell
   git --version
   ```
   
   Nếu hiển thị version (ví dụ: `git version 2.43.0`), Git đã sẵn sàng!

### Cách 2: Tìm Đường Dẫn Git Thủ Công

Nếu cách 1 không được, tìm Git theo các đường dẫn thông dụng:

```powershell
# Thử các đường dẫn thông dụng
& "C:\Program Files\Git\bin\git.exe" --version
# hoặc
& "C:\Program Files (x86)\Git\bin\git.exe" --version
```

Nếu một trong những lệnh trên hoạt động, dùng đường dẫn đó thay vì `git` trong các lệnh bên dưới.

---

## Các Lệnh Push Code

**Mở PowerShell mới** và chạy từng lệnh sau trong thư mục dự án:

```powershell
# Di chuyển vào thư mục dự án
cd c:\projects\dinhle-law

# 1. Khởi tạo Git repository
git init

# 2. Cấu hình thông tin (thay bằng thông tin của bạn)
git config user.name "Your Name"
git config user.email "your.email@example.com"

# 3. Thêm tất cả files
git add .

# 4. Commit với message
git commit -m "DINHLE LAW FIRM - Landing page with social sharing"

# 5. Đổi nhánh thành main
git branch -M main

# 6. Thêm remote repository
git remote add origin https://github.com/tintamquy/dinhlelaw.git

# 7. Push code lên GitHub (có thể cần force nếu repo đã tồn tại)
git push -u origin main --force
```

---

## Xác Thực GitHub

Khi push, GitHub sẽ yêu cầu đăng nhập:

### Option 1: GitHub Desktop (Dễ Nhất)
- Tải về: https://desktop.github.com/
- Đăng nhập và push qua giao diện

### Option 2: Personal Access Token
1. Vào GitHub.com → Settings → Developer settings → Personal access tokens
2. Generate new token (classic)
3. Chọn quyền: `repo`
4. Copy token
5. Dùng token làm password khi git yêu cầu

---

## Files Đã Cập Nhật

✅ **index.html** - Có Open Graph meta tags cho social sharing  
✅ **tru-so-chinh.jpg** - Ảnh trụ sở chính (dùng cho preview)  
✅ **style.css** - Design system  
✅ **script.js** - Interactive features  
✅ **logo.png** - Company logo

---

## Verify Sau Khi Push

1. Truy cập: https://github.com/tintamquy/dinhlelaw
2. Kiểm tra files đã được push
3. Bật GitHub Pages (Settings → Pages → Source: main branch)
4. Website sẽ live tại: https://tintamquy.github.io/dinhlelaw/

---

## Test Social Sharing

Sau khi website live, test preview:

- **Facebook**: https://developers.facebook.com/tools/debug/
- **Twitter**: https://cards-dev.twitter.com/validator
- **LinkedIn**: Share link trực tiếp

Preview sẽ hiển thị ảnh `tru-so-chinh.jpg` khi chia sẻ!

---

**Cần hỗ trợ? Hãy cho tôi biết bước nào gặp vấn đề!**
