# Video Học Tập — Hướng dẫn triển khai

## Tổng quan

Hệ thống gồm 2 file:

| File | Mô tả |
|------|--------|
| `index.html` | Trang web player — giao diện xem video |
| `data.js` | File dữ liệu — nơi bạn dán link video |

## Bước 1: Thêm video — thao tác chính

Mở file `data.js`, tìm đúng môn, thêm tháng/buổi/link theo cấu trúc:

```js
const DATA = {
  "Toán": {
    "Tháng 8": {
      "Buổi 1": [
        "https://cdn2.hocmai.vn/.../playlist_480.m3u8",
        "https://cdn2.hocmai.vn/.../playlist_480.m3u8",
        "https://cdn2.hocmai.vn/.../playlist_480.m3u8",
        "https://cdn2.hocmai.vn/.../playlist_480.m3u8",
      ],
      "Buổi 2": [
        "https://cdn2.hocmai.vn/.../playlist_480.m3u8",
        "https://cdn2.hocmai.vn/.../playlist_480.m3u8",
      ],
    },
    "Tháng 9": {
      "Buổi 3": [
        "https://cdn2.hocmai.vn/.../playlist_480.m3u8",
      ],
    },
  },
  "Văn": {
    ...
  },
};
```

**Quy tắc đơn giản:**
- Mỗi link bọc trong `"..."`, cuối dòng có dấu phẩy `,`
- Thêm buổi: thêm `"Buổi X": [ link1, link2 ],`
- Thêm tháng: thêm `"Tháng X": { "Buổi 1": [...] },`
- **Lưu file → Refresh trang web → Xong!**

---

## Bước 2: Mở xem

### Cách 1: Mở trực tiếp (nhanh nhất)
Mở file `index.html` bằng trình duyệt (kéo thả hoặc double-click).

### Cách 2: Deploy lên GitHub Pages (chia sẻ cho người khác)

1. Tạo repository mới trên [github.com](https://github.com/new) (chọn Public)
2. Upload 2 file: `index.html`, `data.js`
3. Vào **Settings** → **Pages** → Source chọn **Deploy from a branch** → Branch: `main`, folder: `/ (root)` → **Save**
4. Đợi 1-2 phút, trang web sẽ có link dạng:
   ```
   https://ten-cua-ban.github.io/ten-repo/
   ```
5. Gửi link này cho người khác là xem được!

---

## ⚠️ Lưu ý quan trọng

- **Link video có thể hết hạn**: Link m3u8 của HocMai chứa token xác thực (phần `mL8GzQPZ_7R5elUUJdxOBw/1787918414/`). Nếu token hết hạn, video sẽ không phát được → cần lấy link mới.
- **iPhone/iPad**: Safari hỗ trợ HLS gốc.

---

## Xử lý lỗi

| Vấn đề | Giải pháp |
|--------|-----------|
| "Không thể phát video" | Link m3u8 có thể đã hết hạn → lấy link mới |
| Trang trắng | Kiểm tra file `data.js` có lỗi cú pháp không (mở Console bằng F12) |
