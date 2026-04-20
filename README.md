# 📘 CRM SALE – DATA CONTEXT (AppSheet)

## 🎯 Mục tiêu hệ thống
- Quản lý nhân sự (Admin / Leader / Nhân viên)
- Quản lý salon do sale phụ trách
- Theo dõi log làm việc của sale
- Quản lý hợp đồng với salon
- Tính lương & hoa hồng
- Phân quyền theo vai trò và bộ phận

---

# 🧩 DANH SÁCH BẢNG

1. users
2. user_role_map
3. salon
4. log_sale
5. hop_dong_salon
6. bang_luong

---

# 1️⃣ BẢNG users (NHÂN SỰ)

## Mục đích
- Lưu thông tin nhân viên
- Dùng để đăng nhập AppSheet
- Là bảng trung tâm liên kết toàn hệ thống

## Cột dữ liệu

| Cột | Mô tả |
|-----|------|
| id | ID duy nhất |
| email | Email đăng nhập |
| ho_ten | Tên nhân viên |
| so_dien_thoai | SĐT |
| vai_tro | Admin / Leader / Nhân viên |
| bo_phan | Sale / Vận hành |
| luong_cung | Lương cứng |
| ngay_vao_lam | Ngày vào |
| trang_thai | Hoạt động / Nghỉ / Khóa |
| file_hop_dong_maby | File hợp đồng |
| ghi_chu | Ghi chú |
| tao_luc | Thời gian tạo |
| cap_nhat_luc | Thời gian cập nhật |

---

# 2️⃣ BẢNG user_role_map (PHÂN QUYỀN)

## Mục đích
- Dùng để lookup quyền
- Tránh lỗi filter bảng users

## Cột

| Cột | Mô tả |
|-----|------|
| email | Email user |
| vai_tro | Role |
| bo_phan | Bộ phận |

---

# 3️⃣ BẢNG salon

## Mục đích
- Danh sách khách hàng
- Sale tự tạo và quản lý

## Cột

| Cột | Mô tả |
|-----|------|
| id | ID salon |
| ten_salon | Tên salon |
| chu_salon | Chủ salon |
| so_dien_thoai | Liên hệ |
| facebook | Fanpage |
| dia_chi | Địa chỉ |
| khu_vuc | Khu vực |
| nguon_khach | Nguồn lead |
| sale_id | Người phụ trách |
| trang_thai_pipeline | Trạng thái |
| ngay_tiep_can_dau | Ngày bắt đầu |
| ghi_chu | Ghi chú |
| tao_luc | Tạo |
| cap_nhat_luc | Update |

---

# 4️⃣ BẢNG log_sale

## Mục đích
- Lưu lịch sử làm việc với khách

## Cột

| Cột | Mô tả |
|-----|------|
| id | ID |
| salon_id | Salon |
| sale_id | Người thực hiện |
| ngay_gio | Thời gian |
| hinh_thuc | Gọi / Nhắn / Gặp |
| noi_dung | Nội dung |
| ket_qua | Kết quả |
| trang_thai_sau_log | Pipeline |
| lich_hen_tiep_theo | Follow-up |
| tao_luc | Tạo |
| cap_nhat_luc | Update |

---

# 5️⃣ BẢNG hop_dong_salon

## Mục đích
- Quản lý hợp đồng
- Tính hoa hồng

## Cột

| Cột | Mô tả |
|-----|------|
| id | ID |
| salon_id | Salon |
| sale_id | Người chốt |
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

---

# 6️⃣ BẢNG bang_luong

## Mục đích
- Tổng hợp lương

## Cột

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

---

# 🔐 PHÂN QUYỀN

## Admin
- toàn quyền

## Leader
- xem nhân viên cùng bộ phận
- không được sửa

## Nhân viên
- chỉ xem chính mình
- chỉ sửa ngày sinh, giới tính

---

# 🔗 QUAN HỆ

- salon.sale_id → users.id
- log_sale.salon_id → salon.id
- log_sale.sale_id → users.id
- hop_dong_salon.sale_id → users.id
- bang_luong.user_id → users.id

---

# 🚀 FLOW

1. Admin tạo user
2. Sale login
3. Sale tạo salon
4. Sale tạo log
5. Sale chốt hợp đồng
6. Tính hoa hồng
7. Tổng hợp lương


