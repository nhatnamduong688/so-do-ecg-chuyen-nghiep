# Hướng dẫn Quản lý GitHub bằng Tag

**Tag** (thẻ) trong Git giống như một chiếc "kẹp sách" gắn cố định vào một thời điểm lịch sử cụ thể. Nó thường được dùng để đánh dấu các phiên bản phát hành (Releases) như `v1.0`, `v2.0`.

## 1. Tại sao dùng Tag?
- **Cố định phiên bản**: Code thay đổi liên tục, nhưng `v1.0` sẽ mãi mãi trỏ về đúng thời điểm bạn đóng gói sản phẩm đó.
- **Tạo Release trên GitHub**: Khi bạn đẩy tag lên, GitHub sẽ tự động nhận diện để tạo trang "Releases", giúp người khác dễ dàng tải về đúng phiên bản họ cần.

## 2. Các lệnh cơ bản

### a. Tạo Tag
```bash
# Gắn tag v1.0 vào commit hiện tại
git tag -a v1.0 -m "Phien ban dau tien: Hoan thanh 3 so do ECG"
```

### b. Xem Tag
```bash
# Liệt kê các tag đang có
git tag
```

### c. Đẩy Tag lên GitHub
```bash
# Git push bình thường KHÔNG đẩy tag lên. Bạn phải dùng lệnh riêng:
git push origin v1.0

# Hoặc đẩy tất cả các tag
git push origin --tags
```

### d. Xóa Tag
```bash
# Xóa ở máy mình
git tag -d v1.0

# Xóa trên GitHub
git push origin --delete v1.0
```

## 3. Quy trình chuyên nghiệp (Semantic Versioning)
Nên đặt tên tag theo quy chuẩn `vX.Y.Z`:
- **X (Major)**: Thay đổi cực lớn, thay đổi kiến trúc (ví dụ: v1.0 lên v2.0).
- **Y (Minor)**: Thêm tính năng mới (ví dụ: v1.1, v1.2).
- **Z (Patch)**: Sửa lỗi nhỏ (ví dụ: v1.0.1).

## 4. Tìm kiếm và Sử dụng lại

### a. Trên GitHub
Bạn muốn tìm lại code cũ?
1. Vào trang chính của repo.
2. Bấm vào nút **Tags** (bên cạnh số lượng branches/commits).
3. Chọn version bạn muốn (ví dụ `v1.0.0`).
4. Bấm **"Browse files"** để xem code tại thời điểm đó, hoặc tải file zip về.

### b. Ở máy (Terminal)
Tìm kiếm tag:
```bash
# Liệt kê tất cả
git tag

# Tìm kiếm theo mẫu (ví dụ tìm tất cả bản v1.x)
git tag -l "v1.*"
```

Quay về quá khứ (Checkout):
```bash
# Chuyển code trong máy về đúng trạng thái của v1.0.0
git checkout v1.0.0

# Quay trở lại hiện tại (code mới nhất)
git checkout master
```
