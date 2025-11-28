# SƠ ĐỒ USE CASE - HỆ THỐNG QUẢN LÝ MUA BÁN HÀNG ĐIỆN TỬ

## 1. XÁC ĐỊNH TÁC NHÂN (ACTORS)

| STT | Tác nhân | Mô tả |
|:---:|----------|-------|
| 1 | Giám đốc | Quản lý toàn bộ hệ thống, xem báo cáo, quản lý nhân viên |
| 2 | Nhân viên bán hàng | Bán hàng, lập hóa đơn, quản lý khách hàng |
| 3 | Thủ kho | Quản lý nhập hàng, xuất hàng, tồn kho |
| 4 | Nhân viên kỹ thuật | Tiếp nhận và xử lý bảo hành |

---

## 2. SƠ ĐỒ USE CASE TỔNG QUÁT

### Code PlantUML (Copy vào https://www.plantuml.com/plantuml/uml)

```plantuml
@startuml UseCase_TongQuat
left to right direction
skinparam packageStyle rectangle
skinparam actorStyle awesome

title SƠ ĐỒ USE CASE TỔNG QUÁT\nHỆ THỐNG QUẢN LÝ MUA BÁN HÀNG ĐIỆN TỬ

actor "Giám đốc" as GD #LightBlue
actor "Nhân viên\nBán hàng" as NVBH #LightGreen
actor "Thủ kho" as TK #Orange
actor "Nhân viên\nKỹ thuật" as NVKT #Pink

rectangle "HỆ THỐNG QUẢN LÝ MUA BÁN HÀNG ĐIỆN TỬ" {
    usecase "Đăng nhập" as UC0
    usecase "Quản lý sản phẩm" as UC1
    usecase "Quản lý nhập hàng" as UC2
    usecase "Quản lý bán hàng" as UC3
    usecase "Quản lý bảo hành" as UC4
    usecase "Quản lý khách hàng" as UC5
    usecase "Quản lý nhà cung cấp" as UC6
    usecase "Quản lý nhân viên" as UC7
    usecase "Thống kê, báo cáo" as UC8
}

' Giám đốc
GD --> UC0
GD --> UC1
GD --> UC6
GD --> UC7
GD --> UC8

' Nhân viên bán hàng
NVBH --> UC0
NVBH --> UC1
NVBH --> UC3
NVBH --> UC5

' Thủ kho
TK --> UC0
TK --> UC1
TK --> UC2

' Nhân viên kỹ thuật
NVKT --> UC0
NVKT --> UC4
NVKT --> UC5

@enduml
```

---

## 3. SƠ ĐỒ USE CASE CHI TIẾT

### 3.1. Use Case: Đăng nhập và Phân quyền

```plantuml
@startuml UC_DangNhap
left to right direction
skinparam actorStyle awesome

title USE CASE: ĐĂNG NHẬP VÀ PHÂN QUYỀN

actor "Người dùng" as User #LightGray
actor "Giám đốc" as GD #LightBlue

rectangle "Đăng nhập và Phân quyền" {
    usecase "Đăng nhập hệ thống" as UC1
    usecase "Đăng xuất" as UC2
    usecase "Đổi mật khẩu" as UC3
    usecase "Quản lý tài khoản" as UC4
    usecase "Phân quyền người dùng" as UC5
}

User --> UC1
User --> UC2
User --> UC3
GD --> UC4
GD --> UC5
GD --|> User

@enduml
```

---

### 3.2. Use Case: Quản lý sản phẩm

```plantuml
@startuml UC_QuanLySanPham
left to right direction
skinparam actorStyle awesome

title USE CASE: QUẢN LÝ SẢN PHẨM

actor "Giám đốc" as GD #LightBlue
actor "Nhân viên\nBán hàng" as NVBH #LightGreen
actor "Thủ kho" as TK #Orange

rectangle "Quản lý sản phẩm" {
    usecase "Xem danh sách sản phẩm" as UC1
    usecase "Tìm kiếm sản phẩm" as UC2
    usecase "Thêm sản phẩm mới" as UC3
    usecase "Cập nhật thông tin\nsản phẩm" as UC4
    usecase "Xóa sản phẩm" as UC5
    usecase "Quản lý danh mục" as UC6
}

GD --> UC1
GD --> UC2
GD --> UC3
GD --> UC4
GD --> UC5
GD --> UC6

NVBH --> UC1
NVBH --> UC2

TK --> UC1
TK --> UC2
TK --> UC4

@enduml
```

---

### 3.3. Use Case: Quản lý nhập hàng

```plantuml
@startuml UC_QuanLyNhapHang
left to right direction
skinparam actorStyle awesome

title USE CASE: QUẢN LÝ NHẬP HÀNG

actor "Giám đốc" as GD #LightBlue
actor "Thủ kho" as TK #Orange

rectangle "Quản lý nhập hàng" {
    usecase "Lập phiếu nhập hàng" as UC1
    usecase "Xem danh sách\nphiếu nhập" as UC2
    usecase "Tìm kiếm phiếu nhập" as UC3
    usecase "Xem chi tiết phiếu nhập" as UC4
    usecase "Hủy phiếu nhập" as UC5
    usecase "In phiếu nhập" as UC6
}

TK --> UC1
TK --> UC2
TK --> UC3
TK --> UC4
TK --> UC6

GD --> UC2
GD --> UC3
GD --> UC4
GD --> UC5

@enduml
```

---

### 3.4. Use Case: Quản lý bán hàng

```plantuml
@startuml UC_QuanLyBanHang
left to right direction
skinparam actorStyle awesome

title USE CASE: QUẢN LÝ BÁN HÀNG

actor "Nhân viên\nBán hàng" as NVBH #LightGreen
actor "Giám đốc" as GD #LightBlue

rectangle "Quản lý bán hàng" {
    usecase "Lập hóa đơn bán hàng" as UC1
    usecase "Tìm kiếm sản phẩm" as UC2
    usecase "Áp dụng khuyến mãi" as UC3
    usecase "Thanh toán" as UC4
    usecase "In hóa đơn" as UC5
    usecase "Xem lịch sử bán hàng" as UC6
    usecase "Hủy hóa đơn" as UC7
}

NVBH --> UC1
NVBH --> UC2
NVBH --> UC4
NVBH --> UC5
NVBH --> UC6

UC1 ..> UC2 : <<include>>
UC1 ..> UC3 : <<extend>>
UC1 ..> UC4 : <<include>>

GD --> UC6
GD --> UC7

@enduml
```

---

### 3.5. Use Case: Quản lý bảo hành

```plantuml
@startuml UC_QuanLyBaoHanh
left to right direction
skinparam actorStyle awesome

title USE CASE: QUẢN LÝ BẢO HÀNH

actor "Nhân viên\nKỹ thuật" as NVKT #Pink
actor "Giám đốc" as GD #LightBlue

rectangle "Quản lý bảo hành" {
    usecase "Tiếp nhận bảo hành" as UC1
    usecase "Tra cứu thông tin\nbảo hành" as UC2
    usecase "Cập nhật trạng thái\nxử lý" as UC3
    usecase "Trả hàng bảo hành" as UC4
    usecase "Xem lịch sử bảo hành" as UC5
    usecase "In phiếu bảo hành" as UC6
}

NVKT --> UC1
NVKT --> UC2
NVKT --> UC3
NVKT --> UC4
NVKT --> UC5
NVKT --> UC6

GD --> UC2
GD --> UC5

@enduml
```

---

### 3.6. Use Case: Quản lý khách hàng

```plantuml
@startuml UC_QuanLyKhachHang
left to right direction
skinparam actorStyle awesome

title USE CASE: QUẢN LÝ KHÁCH HÀNG

actor "Nhân viên\nBán hàng" as NVBH #LightGreen
actor "Nhân viên\nKỹ thuật" as NVKT #Pink

rectangle "Quản lý khách hàng" {
    usecase "Thêm khách hàng mới" as UC1
    usecase "Cập nhật thông tin\nkhách hàng" as UC2
    usecase "Tìm kiếm khách hàng" as UC3
    usecase "Xem lịch sử mua hàng" as UC4
    usecase "Xóa khách hàng" as UC5
}

NVBH --> UC1
NVBH --> UC2
NVBH --> UC3
NVBH --> UC4
NVBH --> UC5

NVKT --> UC3
NVKT --> UC4

@enduml
```

---

### 3.7. Use Case: Quản lý nhà cung cấp

```plantuml
@startuml UC_QuanLyNCC
left to right direction
skinparam actorStyle awesome

title USE CASE: QUẢN LÝ NHÀ CUNG CẤP

actor "Giám đốc" as GD #LightBlue

rectangle "Quản lý nhà cung cấp" {
    usecase "Thêm nhà cung cấp" as UC1
    usecase "Cập nhật thông tin NCC" as UC2
    usecase "Xóa nhà cung cấp" as UC3
    usecase "Tìm kiếm NCC" as UC4
    usecase "Xem lịch sử nhập hàng\ntừ NCC" as UC5
}

GD --> UC1
GD --> UC2
GD --> UC3
GD --> UC4
GD --> UC5

@enduml
```

---

### 3.8. Use Case: Quản lý nhân viên

```plantuml
@startuml UC_QuanLyNhanVien
left to right direction
skinparam actorStyle awesome

title USE CASE: QUẢN LÝ NHÂN VIÊN

actor "Giám đốc" as GD #LightBlue

rectangle "Quản lý nhân viên" {
    usecase "Thêm nhân viên mới" as UC1
    usecase "Cập nhật thông tin\nnhân viên" as UC2
    usecase "Xóa nhân viên" as UC3
    usecase "Tìm kiếm nhân viên" as UC4
    usecase "Tạo tài khoản\nđăng nhập" as UC5
    usecase "Phân quyền" as UC6
}

GD --> UC1
GD --> UC2
GD --> UC3
GD --> UC4
GD --> UC5
GD --> UC6

UC1 ..> UC5 : <<include>>
UC5 ..> UC6 : <<include>>

@enduml
```

---

### 3.9. Use Case: Thống kê và Báo cáo

```plantuml
@startuml UC_ThongKeBaoCao
left to right direction
skinparam actorStyle awesome

title USE CASE: THỐNG KÊ VÀ BÁO CÁO

actor "Giám đốc" as GD #LightBlue

rectangle "Thống kê và Báo cáo" {
    usecase "Báo cáo doanh thu\ntheo ngày" as UC1
    usecase "Báo cáo doanh thu\ntheo tháng" as UC2
    usecase "Báo cáo doanh thu\ntheo năm" as UC3
    usecase "Báo cáo tồn kho" as UC4
    usecase "Thống kê sản phẩm\nbán chạy" as UC5
    usecase "Báo cáo bảo hành" as UC6
    usecase "Xuất báo cáo\n(Excel/PDF)" as UC7
}

GD --> UC1
GD --> UC2
GD --> UC3
GD --> UC4
GD --> UC5
GD --> UC6
GD --> UC7

UC1 ..> UC7 : <<extend>>
UC2 ..> UC7 : <<extend>>
UC3 ..> UC7 : <<extend>>
UC4 ..> UC7 : <<extend>>

@enduml
```

---

## 4. BẢNG TỔNG HỢP USE CASE VÀ TÁC NHÂN

| STT | Use Case | Giám đốc | NV Bán hàng | Thủ kho | NV Kỹ thuật |
|:---:|----------|:--------:|:-----------:|:-------:|:-----------:|
| 1 | Đăng nhập hệ thống | ✓ | ✓ | ✓ | ✓ |
| 2 | Đăng xuất | ✓ | ✓ | ✓ | ✓ |
| 3 | Đổi mật khẩu | ✓ | ✓ | ✓ | ✓ |
| 4 | Quản lý tài khoản | ✓ | | | |
| 5 | Phân quyền người dùng | ✓ | | | |
| 6 | Xem danh sách sản phẩm | ✓ | ✓ | ✓ | |
| 7 | Tìm kiếm sản phẩm | ✓ | ✓ | ✓ | |
| 8 | Thêm sản phẩm mới | ✓ | | | |
| 9 | Cập nhật thông tin SP | ✓ | | ✓ | |
| 10 | Xóa sản phẩm | ✓ | | | |
| 11 | Quản lý danh mục | ✓ | | | |
| 12 | Lập phiếu nhập hàng | | | ✓ | |
| 13 | Xem danh sách phiếu nhập | ✓ | | ✓ | |
| 14 | Hủy phiếu nhập | ✓ | | | |
| 15 | Lập hóa đơn bán hàng | | ✓ | | |
| 16 | Thanh toán | | ✓ | | |
| 17 | In hóa đơn | | ✓ | | |
| 18 | Xem lịch sử bán hàng | ✓ | ✓ | | |
| 19 | Hủy hóa đơn | ✓ | | | |
| 20 | Tiếp nhận bảo hành | | | | ✓ |
| 21 | Tra cứu thông tin BH | ✓ | | | ✓ |
| 22 | Cập nhật trạng thái BH | | | | ✓ |
| 23 | Trả hàng bảo hành | | | | ✓ |
| 24 | Thêm khách hàng mới | | ✓ | | |
| 25 | Tìm kiếm khách hàng | | ✓ | | ✓ |
| 26 | Xem lịch sử mua hàng | | ✓ | | ✓ |
| 27 | Thêm nhà cung cấp | ✓ | | | |
| 28 | Cập nhật thông tin NCC | ✓ | | | |
| 29 | Xóa nhà cung cấp | ✓ | | | |
| 30 | Thêm nhân viên mới | ✓ | | | |
| 31 | Cập nhật thông tin NV | ✓ | | | |
| 32 | Xóa nhân viên | ✓ | | | |
| 33 | Báo cáo doanh thu | ✓ | | | |
| 34 | Báo cáo tồn kho | ✓ | | | |
| 35 | Thống kê SP bán chạy | ✓ | | | |
| 36 | Xuất báo cáo Excel/PDF | ✓ | | | |

---

## 5. HƯỚNG DẪN VẼ SƠ ĐỒ

### Cách 1: Dùng PlantUML Online
1. Truy cập: https://www.plantuml.com/plantuml/uml
2. Copy code PlantUML ở trên
3. Paste vào ô nhập liệu
4. Nhấn "Submit" để xem sơ đồ
5. Click chuột phải vào hình → Save image

### Cách 2: Dùng Draw.io
1. Truy cập: https://app.diagrams.net/
2. Chọn "Create New Diagram"
3. Chọn template "UML" → "Use Case Diagram"
4. Vẽ theo mô tả ở trên

### Cách 3: Dùng StarUML
1. Mở StarUML
2. Tạo project mới
3. Add "Use Case Diagram"
4. Kéo thả các Actor và Use Case theo mô tả

---

## 6. GHI CHÚ KÝ HIỆU

| Ký hiệu | Ý nghĩa |
|---------|---------|
| Actor (hình người) | Tác nhân tương tác với hệ thống |
| Oval (hình elip) | Use Case - chức năng của hệ thống |
| Đường thẳng | Quan hệ giữa Actor và Use Case |
| <<include>> | Use Case này BẮT BUỘC gọi Use Case kia |
| <<extend>> | Use Case này CÓ THỂ mở rộng Use Case kia |
| Generalization (mũi tên rỗng) | Quan hệ kế thừa |

