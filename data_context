# 📘 CRM SALE – DATA CONTEXT (Final Version)

## 🎯 Mục tiêu hệ thống
- Quản lý nhân sự (Admin / Leader / Nhân viên)
- Quản lý salon do sale phụ trách
- Theo dõi log làm việc của sale
- Quản lý hợp đồng với salon
- Tính lương & hoa hồng
- Phân quyền theo vai trò và bộ phận

---

## 🧩 Danh sách bảng

### Bảng chính
1. `users`
2. `salon`
3. `log_sale`
4. `hop_dong_salon`
5. `bang_luong`

### View
- `vw_salon_van_hanh`

---

## 1️⃣ BẢNG `users` (NHÂN SỰ)

### Mục đích
- Lưu thông tin nhân viên
- Dùng để đăng nhập AppSheet
- Là bảng trung tâm phân quyền toàn hệ thống

### Cột dữ liệu

| Cột | Mô tả |
|-----|------|
| id | ID duy nhất |
| email | Email đăng nhập |
| ho_ten | Tên nhân viên |
| so_dien_thoai | SĐT |
| ngay_sinh | Ngày sinh |
| vai_tro | Admin / Leader / Nhân viên |
| bo_phan | Sale / Vận hành / Dev |
| luong_cung | Lương cứng |
| ngay_vao_lam | Ngày vào |
| trang_thai | Đang làm / Đã nghỉ |
| file_hop_dong | Link hợp đồng nhân sự |
| ghi_chu | Ghi chú |
| tao_luc | Thời gian tạo |
| cap_nhat_luc | Thời gian cập nhật |

### Quyền

#### Admin
- Full quyền

#### Leader
- Xem nhân sự theo phạm vi được phép
- Không sửa người khác

#### Nhân viên
- Chỉ xem chính mình
- Chỉ được sửa:
  - `so_dien_thoai`
  - `ngay_sinh`

### Quy tắc đặc biệt
- User `Đã nghỉ`:
  - vẫn giữ dữ liệu
  - ẩn khỏi danh sách active
  - không dùng để chọn trong hệ thống

---

## 2️⃣ BẢNG `salon`

### Mục đích
- Danh sách khách hàng (lead)
- Sale phụ trách và chăm sóc

### Cột dữ liệu

| Cột | Mô tả |
|-----|------|
| id | ID salon |
| ten_salon | Tên salon |
| chu_salon | Chủ salon |
| so_dien_thoai | SĐT liên hệ |
| hotline | Hotline salon |
| facebook | Fanpage |
| dia_chi | Địa chỉ |
| khu_vuc | Khu vực |
| nguon_khach | Nguồn lead |
| sale_id | Sale phụ trách |
| trang_thai_pipeline | Trạng thái |
| ngay_tiep_can_dau | Ngày tiếp cận |
| ghi_chu | Ghi chú |
| tao_luc | Tạo |
| cap_nhat_luc | Update |

### Quyền

#### Admin
- Full quyền

#### Nhân viên Sale
- Chỉ xem salon của mình
- Tạo / sửa salon của mình

#### Leader Sale
- Xem toàn bộ salon bộ phận sale
- Sửa salon
- Phân salon cho sale

#### Vận hành
- Không dùng bảng này trực tiếp để thao tác

### Quy tắc nghiệp vụ

#### Ownership
- 1 salon = 1 sale phụ trách

#### Chống trùng
- Trùng khi đồng thời trùng:
  - `dia_chi`
  - `so_dien_thoai`

#### Khi tạo salon
- Nhân viên Sale → tự gán `sale_id = người đang đăng nhập`
- Leader/Admin → được chọn `sale_id`

### Pipeline
- `Mới tạo`
- `Đang tiếp cận`
- `Đang chăm`
- `Đã chốt`
- `Hủy`

---

## 3️⃣ VIEW `vw_salon_van_hanh`

### Mục đích
- Phục vụ bộ phận vận hành
- Tách khỏi bảng gốc để khóa quyền

### Dữ liệu
- Hiển thị toàn bộ cột của `salon`

### Quyền

#### Nhân viên vận hành
- Xem tất cả salon
- Không sửa

#### Leader vận hành
- Xem tất cả salon
- Không sửa

---

## 4️⃣ BẢNG `log_sale`

### Mục đích
- Lưu lịch sử làm việc với salon

### Cột dữ liệu

| Cột | Mô tả |
|-----|------|
| id | ID |
| salon_id | Salon |
| sale_id | Người tạo |
| ngay_gio | Thời gian |
| noi_dung | Nội dung |
| tao_luc | Tạo |
| cap_nhat_luc | Update |

### Quyền

#### Admin
- Xem / sửa tất cả

#### Nhân viên Sale
- Chỉ xem log của mình
- Chỉ sửa log của mình

#### Leader Sale
- Xem tất cả log bộ phận sale
- Không sửa

#### Vận hành
- Không xem

---

## 5️⃣ BẢNG `hop_dong_salon`

### Mục đích
- Quản lý hợp đồng
- Tính hoa hồng

### Cột dữ liệu

| Cột | Mô tả |
|-----|------|
| id | ID |
| salon_id | Salon |
| sale_id | Sale phụ trách |
| ma_hop_dong | Mã |
| ngay_chot | Ngày |
| goi_dich_vu | Gói |
| gia_tri_hop_dong | Giá trị |
| doanh_thu_thuc_nhan | Thực nhận |
| ty_le_hoa_hong | % |
| so_tien_hoa_hong | Hoa hồng |
| trang_thai_hop_dong | Trạng thái |
| file_hop_dong | File |
| ghi_chu | Ghi chú |
| tao_luc | Tạo |
| cap_nhat_luc | Update |

### Quyền

#### Admin
- Full quyền

#### Leader Sale
- Xem tất cả hợp đồng bộ phận sale
- Tạo hợp đồng
- Sửa hợp đồng

#### Nhân viên Sale
- Không xem
- Không tạo
- Không sửa

#### Vận hành
- Không xem

---

## 6️⃣ BẢNG `bang_luong`

### Mục đích
- Tổng hợp lương & hoa hồng

### Cột dữ liệu

| Cột | Mô tả |
|-----|------|
| id | ID |
| user_id | Nhân viên |
| thang | Tháng |
| nam | Năm |
| luong_cung | Lương |
| tong_hoa_hong | Hoa hồng |
| tong_thu_nhap | Tổng |
| khau_tru | Trừ |
| thuc_linh | Thực nhận |
| trang_thai | Trạng thái |
| ghi_chu | Ghi chú |
| tao_luc | Tạo |
| cap_nhat_luc | Update |

### Quyền

#### Admin
- Full quyền

#### Nhân viên
- Chỉ xem lương chính mình

#### Leader
- Chỉ xem lương của chính leader
- Không xem lương người khác

---

## 🔗 Quan hệ
- `salon.sale_id` → `users.id`
- `log_sale.salon_id` → `salon.id`
- `log_sale.sale_id` → `users.id`
- `hop_dong_salon.salon_id` → `salon.id`
- `hop_dong_salon.sale_id` → `users.id`
- `bang_luong.user_id` → `users.id`

---

## 🚀 Flow hệ thống
1. Admin tạo user
2. Sale đăng nhập
3. Sale tạo salon
4. Sale cập nhật log
5. Leader theo dõi & quản lý
6. Leader tạo hợp đồng khi chốt
7. Hệ thống tính hoa hồng
8. Tổng hợp bảng lương

---

## ✅ Ghi chú kiến trúc
- Không dùng `user_role_map`
- Phân quyền dựa vào:
  - `vai_tro`
  - `bo_phan`
- Tách view `vw_salon_van_hanh` để:
  - giảm rủi ro sửa nhầm
  - đơn giản hóa quyền vận hành
- Dữ liệu được giữ lại khi nhân sự nghỉ để phục vụ audit
