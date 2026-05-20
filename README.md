# 📦 MyApp — Download Center

Web tải xuống tự động kết nối với **GitHub Releases**.  
Khi bạn tạo Release mới, trang web tự cập nhật ngay lập tức.

---

## 🚀 Hướng dẫn cài đặt (5 phút)

### Bước 1 — Tạo repository trên GitHub
1. Vào [github.com](https://github.com) → **New repository**
2. Đặt tên repo (ví dụ: `myapp-download`)
3. Chọn **Public** → Create

### Bước 2 — Upload các file này lên repo
```
myapp-download/
├── index.html              ← Trang web download
├── README.md
└── .github/
    └── workflows/
        └── deploy.yml      ← Tự động deploy
```

### Bước 3 — Sửa cấu hình trong `index.html`
Mở `index.html`, tìm phần cấu hình (dòng ~230):

```javascript
const GITHUB_USER = "YOUR_USERNAME";  // ← GitHub username của bạn
const GITHUB_REPO = "YOUR_REPO";      // ← Tên repo chứa file release
const APP_NAME    = "MyApp";          // ← Tên app của bạn
```

> ⚠️ `GITHUB_REPO` là repo chứa **file release** (có thể khác repo này)

### Bước 4 — Bật GitHub Pages
1. Vào repo → **Settings** → **Pages**
2. Source: chọn **GitHub Actions**
3. Save

### Bước 5 — Upload file app lên Release
1. Vào repo chứa ứng dụng → **Releases** → **Draft a new release**
2. **Tag**: `v1.0.0` (hoặc bất kỳ version nào)
3. **Attach binaries**: kéo file `.exe`, `.dmg`, `.apk`... vào
4. Viết changelog vào ô mô tả (hỗ trợ markdown)
5. **Publish release**

🎉 Trang web tự động cập nhật trong vài giây!

---

## 📋 Format Changelog (trong Release body)

```markdown
- Thêm tính năng đăng nhập Google
- Fix lỗi crash khi mở file lớn
- New: Giao diện dark mode
- Cải thiện tốc độ tải trang
```

Trang web tự nhận dạng:
- Từ `new`, `thêm`, `add` → badge **NEW** (xanh lá)
- Từ `fix`, `sửa`, `bug` → badge **FIX** (vàng)
- Còn lại → badge **IMPROVE** (xanh cyan)

---

## 🗂️ Tên file release — Nhận dạng nền tảng

| Tên file chứa...         | Hiển thị       |
|--------------------------|----------------|
| `windows`, `win`, `.exe`, `.msi` | 🪟 Windows |
| `mac`, `darwin`, `.dmg`, `.pkg`  | 🍎 macOS   |
| `linux`, `.deb`, `.rpm`          | 🐧 Linux   |
| `.apk`                           | 🤖 Android |
| `.zip`, `.tar.gz`                | 📦 All     |

---

## 🔧 Tùy chỉnh nâng cao

### Đổi tên & màu sắc
Sửa trong `index.html`:
```css
:root {
  --accent: #00e5ff;   /* Màu chủ đạo (cyan) */
  --accent2: #7c3aed;  /* Màu phụ (tím) */
}
```

### Dùng repo riêng cho releases
Bạn có thể:
- **Repo A**: chứa `index.html` (trang web)
- **Repo B**: chứa releases của app

Chỉ cần set `GITHUB_REPO = "repo-B"` trong cấu hình.

---

## ❓ FAQ

**Q: Trang web có bị giới hạn lượt xem không?**  
A: GitHub Pages miễn phí cho repo public, không giới hạn lượt xem.

**Q: API GitHub có bị rate limit không?**  
A: 60 requests/giờ với IP không đăng nhập. Đủ dùng cho trang download thông thường.

**Q: Có thể dùng cho repo Private không?**  
A: GitHub Pages chỉ hoạt động với repo Public (gói miễn phí).

---

Made with ❤️ — Powered by GitHub Pages & GitHub Releases
