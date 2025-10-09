<!-- # Docs -->

# Use Case Diagrams

Tài liệu này mô tả các use case diagrams cho hệ thống Tourist Management System (TMS), bao gồm các actor chính và chức năng của họ.

## Actors

Hệ thống TMS có 3 loại actor chính:

### 1. [Customer](./use-case/customer.html)

Khách hàng sử dụng hệ thống để:

- Xem và tìm kiếm sản phẩm du lịch
- Quản lý giỏ hàng
- Đặt tour và thanh toán
- Đánh giá và review
- Quản lý tài khoản cá nhân

### 2. [Staff](./use-case/staff.html)

Nhân viên quản lý các hoạt động hàng ngày:

- Quản lý người dùng
- Quản lý sản phẩm du lịch
- Xử lý đơn đặt tour
- Kiểm duyệt đánh giá
- Xem báo cáo thống kê

### 3. [Admin](./use-case/admin.html)

Quản trị viên có quyền cao nhất:

- Quản lý toàn bộ người dùng và nhân viên
- Quản lý sản phẩm và danh mục
- Xử lý đơn đặt tour và hoàn tiền
- Quản lý hệ thống
- Xem báo cáo tổng hợp
- Cấu hình hệ thống

## Use Case Hierarchy

```
TMS System
├── Authentication & Authorization
│   ├── Login/Logout
│   ├── Register
│   └── Password Management
│
├── Product Management
│   ├── View Products (All roles)
│   ├── CRUD Products (Staff, Admin)
│   └── Category Management (Admin)
│
├── Booking Management
│   ├── Create Booking (Customer)
│   ├── View Bookings (All roles)
│   ├── Update Status (Staff, Admin)
│   └── Process Refund (Staff, Admin)
│
├── Review Management
│   ├── CRUD Review (Customer)
│   ├── Moderate Reviews (Staff, Admin)
│   └── Manage Policies (Admin)
│
├── User Management
│   ├── View Users (Staff, Admin)
│   ├── Update User Status (Staff, Admin)
│   └── Full CRUD (Admin)
│
├── Staff Management
│   └── Full CRUD (Admin only)
│
├── Reporting
│   ├── Basic Reports (Staff)
│   └── Comprehensive Analytics (Admin)
│
└── System Configuration
    └── Settings & Config (Admin only)
```

## Permission Matrix

| Feature         | Customer | Staff        | Admin   |
| --------------- | -------- | ------------ | ------- |
| View Products   | ✅       | ✅           | ✅      |
| Manage Cart     | ✅       | ❌           | ❌      |
| Create Booking  | ✅       | ❌           | ❌      |
| Manage Products | ❌       | ✅           | ✅      |
| Manage Users    | ❌       | 👁️ View Only | ✅      |
| Manage Staff    | ❌       | ❌           | ✅      |
| View Reports    | ❌       | ✅ Basic     | ✅ Full |
| System Config   | ❌       | ❌           | ✅      |

## Notes

- Tất cả use case diagrams sử dụng PlantUML với theme `mars`
- Mỗi diagram có `diagram id` để tránh storage leaks
- Use cases được nhóm theo chức năng và quyền hạn
- Chi tiết các sequence/activity diagrams cho từng use case xem tại `/sequence` và `/activity`
