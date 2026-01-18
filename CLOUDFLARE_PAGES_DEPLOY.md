# Deploy DINHLE LAW FIRM lên Cloudflare Pages với Custom Domain

## 🎯 Mục Tiêu
Deploy website lên **lawfirm.dinhlegroup.vn** sử dụng Cloudflare Pages

---

## 📋 Yêu Cầu
- ✅ GitHub repository: https://github.com/tintamquy/dinhlelaw
- ✅ Domain dinhlegroup.vn đã có trên Cloudflare
- ✅ Tài khoản Cloudflare có quyền quản lý domain

---

## 🚀 Bước 1: Tạo Cloudflare Pages Project

### 1.1. Truy cập Cloudflare Dashboard
1. Đăng nhập vào: https://dash.cloudflare.com/
2. Chọn **"Workers & Pages"** ở sidebar bên trái
3. Click **"Create application"**
4. Chọn tab **"Pages"**
5. Click **"Connect to Git"**

### 1.2. Kết nối GitHub Repository
1. Click **"Connect GitHub"** (nếu chưa kết nối)
2. Authorize Cloudflare truy cập GitHub của bạn
3. Chọn repository: **tintamquy/dinhlelaw**
4. Click **"Begin setup"**

### 1.3. Cấu hình Build Settings

**Project name:** `dinhle-law` (hoặc tên bạn muốn)

**Production branch:** `main`

**Build settings:**
- **Framework preset:** None (vì là static HTML)
- **Build command:** (để trống)
- **Build output directory:** `/` (root directory)

> 💡 **Lưu ý:** Website của bạn là static HTML nên không cần build command

**Environment variables:** (không cần)

4. Click **"Save and Deploy"**

### 1.4. Chờ Deploy Hoàn Tất
- Cloudflare sẽ tự động deploy
- Thời gian: ~1-2 phút
- Theo dõi progress trong dashboard

---

## 🌐 Bước 2: Cấu hình Custom Domain (lawfirm.dinhlegroup.vn)

### 2.1. Thêm Custom Domain vào Pages Project

1. Sau khi deploy xong, vào **Pages project** vừa tạo
2. Click tab **"Custom domains"**
3. Click **"Set up a custom domain"**
4. Nhập domain: `lawfirm.dinhlegroup.vn`
5. Click **"Continue"**

### 2.2. Xác Nhận Domain Ownership

Cloudflare sẽ **tự động nhận diện** vì `dinhlegroup.vn` đã có trên cùng tài khoản.

**Cloudflare sẽ hiển thị 2 options:**

#### Option 1: Tự động cấu hình DNS (Recommended) ✅
- Cloudflare tự động thêm DNS record
- Click **"Activate domain"**
- ✅ **CHỌN OPTION NÀY** - Đơn giản nhất!

#### Option 2: Thêm DNS record thủ công
Nếu option 1 không hoạt động, làm theo bước dưới:

---

## 🔧 Bước 3: Cấu hình DNS (Nếu Cần Thủ Công)

### 3.1. Truy cập DNS Settings

1. Trong Cloudflare Dashboard, chọn domain **dinhlegroup.vn**
2. Click tab **"DNS"** > **"Records"**

### 3.2. Thêm CNAME Record

Click **"Add record"** và nhập:

| Field | Value |
|-------|-------|
| **Type** | CNAME |
| **Name** | `lawfirm` |
| **Target** | `dinhle-law.pages.dev` (thay bằng URL Pages của bạn) |
| **Proxy status** | ✅ Proxied (bật cloud orange) |
| **TTL** | Auto |

> 💡 **Lưu ý:** URL `dinhle-law.pages.dev` sẽ được hiển thị trong Cloudflare Pages dashboard của bạn

### 3.3. Save DNS Record

Click **"Save"** để lưu

---

## ⚡ Bước 4: Kích Hoạt và Verify

### 4.1. Quay lại Pages Project

1. Vào **Workers & Pages** > chọn project `dinhle-law`
2. Tab **"Custom domains"**
3. Kiểm tra status của `lawfirm.dinhlegroup.vn`

**Status sẽ là:**
- ⏳ **"Pending"** - Đang cấu hình
- ⏳ **"Pending certificate"** - Đang tạo SSL
- ✅ **"Active"** - Đã hoàn tất!

### 4.2. Thời Gian Propagation

- **DNS Propagation:** 5-10 phút (thường ngay lập tức vì cùng Cloudflare)
- **SSL Certificate:** 2-5 phút
- **Tổng thời gian:** ~10-15 phút

---

## 🎉 Bước 5: Kiểm Tra Website

### 5.1. Truy cập URL

Mở trình duyệt và truy cập:
- 🌐 **https://lawfirm.dinhlegroup.vn**

### 5.2. Verify SSL Certificate

1. Click vào ổ khóa trên address bar
2. Kiểm tra: **"Certificate is valid"**
3. Issued by: **Cloudflare**

### 5.3. Test Social Sharing

**Facebook Debugger:**
- URL: https://developers.facebook.com/tools/debug/
- Paste: `https://lawfirm.dinhlegroup.vn`
- Click **"Scrape Again"**
- Verify: Ảnh `tru-so-chinh.jpg` hiển thị

**Twitter Card:**
- URL: https://cards-dev.twitter.com/validator
- Paste: `https://lawfirm.dinhlegroup.vn`
- Verify: Preview card đẹp

---

## 🔄 Bước 6: Cập Nhật Meta Tags (Nếu Cần)

Nếu social sharing preview không hiển thị đúng, cập nhật meta tags trong `index.html`:

```html
<!-- Thay đổi URL từ GitHub Pages sang subdomain -->
<meta property="og:url" content="https://lawfirm.dinhlegroup.vn">
<meta property="og:image" content="https://lawfirm.dinhlegroup.vn/tru-so-chinh.jpg">

<meta name="twitter:url" content="https://lawfirm.dinhlegroup.vn">
<meta name="twitter:image" content="https://lawfirm.dinhlegroup.vn/tru-so-chinh.jpg">
```

Sau đó push lên GitHub:

```powershell
& "C:\Program Files\Git\bin\git.exe" add index.html
& "C:\Program Files\Git\bin\git.exe" commit -m "Update meta tags for Cloudflare Pages domain"
& "C:\Program Files\Git\bin\git.exe" push
```

Cloudflare Pages sẽ tự động deploy lại (1-2 phút).

---

## 🎯 Expected Results

Sau khi hoàn tất tất cả bước:

✅ **Website live tại:** https://lawfirm.dinhlegroup.vn  
✅ **SSL Certificate:** Active (HTTPS tự động)  
✅ **Auto Deploy:** Mỗi lần push code lên GitHub main branch  
✅ **CDN:** Toàn cầu qua Cloudflare network  
✅ **Social Sharing:** Preview đẹp với ảnh trụ sở chính

---

## 📊 Cloudflare Pages Features

### Automatic Deployments
- ✅ Mỗi khi push lên `main` branch → Auto deploy
- ✅ Preview deployments cho pull requests
- ✅ Rollback dễ dàng về version trước

### Performance
- ✅ **Global CDN:** 300+ data centers worldwide
- ✅ **Brotli Compression:** Tự động
- ✅ **HTTP/3:** Enabled
- ✅ **DDoS Protection:** Included

### Analytics (Free)
- Vào tab **"Analytics"** trong Pages project
- Xem: Page views, visitors, bandwidth

---

## 🔧 Troubleshooting

### Issue 1: "Domain already exists"
**Nguyên nhân:** Domain đã được dùng cho project khác

**Giải pháp:**
1. Kiểm tra các Pages projects khác
2. Remove domain từ project cũ
3. Thêm lại vào project mới

### Issue 2: SSL Certificate pending quá lâu
**Nguyên nhân:** DNS chưa propagate

**Giải pháp:**
1. Verify DNS record đúng
2. Check DNS propagation: https://dnschecker.org/
3. Đợi thêm 10-15 phút

### Issue 3: "Error 522" khi truy cập
**Nguyên nhân:** Pages deployment chưa xong

**Giải pháp:**
1. Vào Pages project dashboard
2. Kiểm tra deployment status
3. Nếu failed, click **"Retry deployment"**

---

## 💡 Tips & Best Practices

### 1. Branch Protection
Trong GitHub repository settings:
- Protect `main` branch
- Require pull request reviews
- Prevent accidental force pushes

### 2. Preview Deployments
Cloudflare tự động tạo preview URL cho mỗi commit:
- Format: `<commit-hash>.dinhle-law.pages.dev`
- Test trước khi merge vào main

### 3. Web Analytics (Optional)
Enable Cloudflare Web Analytics (free):
1. Pages project → **"Web Analytics"**
2. Click **"Enable"**
3. Xem real-time traffic

### 4. Environment Variables
Nếu cần thêm config (ví dụ: API keys):
1. Pages project → **"Settings"** → **"Environment variables"**
2. Add variables
3. Redeploy

---

## 📞 Next Steps After Deploy

### 1. Update Company Materials
- ✅ Business cards → lawfirm.dinhlegroup.vn
- ✅ Email signatures
- ✅ Social media profiles

### 2. SEO Optimization
- Submit sitemap to Google Search Console
- Add to Google My Business
- Update Bing Webmaster Tools

### 3. Monitoring
- Set up Cloudflare Email Alerts for:
  - High error rates
  - Traffic spikes
  - SSL expiry (auto-renew, nhưng có alert)

---

## 📋 Quick Reference

### Cloudflare Dashboard URLs
- **Pages Projects:** https://dash.cloudflare.com/pages
- **DNS Management:** https://dash.cloudflare.com/ → dinhlegroup.vn → DNS
- **Analytics:** Pages Project → Analytics tab

### Important Endpoints
- **Production:** https://lawfirm.dinhlegroup.vn
- **Cloudflare Pages:** https://dinhle-law.pages.dev
- **GitHub Repo:** https://github.com/tintamquy/dinhlelaw

### Support Resources
- **Cloudflare Docs:** https://developers.cloudflare.com/pages/
- **Community:** https://community.cloudflare.com/
- **Status:** https://www.cloudflarestatus.com/

---

## ✅ Deployment Checklist

- [ ] Cloudflare Pages project created
- [ ] GitHub repository connected
- [ ] Initial deployment successful
- [ ] Custom domain `lawfirm.dinhlegroup.vn` added
- [ ] DNS CNAME record created
- [ ] SSL certificate active
- [ ] Website accessible via HTTPS
- [ ] Social sharing preview verified
- [ ] Meta tags updated with correct domain
- [ ] Auto-deployment tested (push to GitHub)

---

**Chúc mừng! Website của bạn đã production-ready trên Cloudflare Pages! 🚀**

Nếu cần hỗ trợ thêm, hãy cho tôi biết bước nào bạn gặp khó khăn!
