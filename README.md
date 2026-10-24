# NongNghiep – Mobile Prototype

## 1. Giới thiệu

NongNghiep Mobile Prototype là bộ giao diện mô phỏng ứng dụng quản lý sản xuất nông nghiệp, tập trung vào hai lĩnh vực **Trồng trọt** và **Thủy sản**.

Bộ prototype được xây dựng nhằm trực quan hóa giao diện, tổ chức màn hình theo vai trò người dùng và mô phỏng những quy trình nghiệp vụ chính trước khi phát triển ứng dụng thực tế.

Sản phẩm được thực hiện trong quá trình thực tập doanh nghiệp, phục vụ nghiên cứu nghiệp vụ, thiết kế UI/UX và đánh giá trải nghiệm người dùng.

## 2. Phạm vi prototype

### 2.1. Mobile Trồng trọt

Bao gồm 8 vai trò:

1. Công nhân
2. Tổ trưởng
3. Kỹ sư
4. Quản lý nông trường
5. Điều phối thu mua
6. Tài xế
7. QC
8. Thủ kho

Các nhóm nghiệp vụ được mô phỏng bao gồm quản lý công việc, nhật ký canh tác, thu hoạch, cân, thu mua, vận chuyển, kiểm tra chất lượng và quản lý kho.

### 2.2. Mobile Thủy sản

Bao gồm 7 vai trò:

1. Công nhân
2. Tổ trưởng
3. Kỹ sư
4. Quản lý trại
5. Tài xế
6. QC
7. Thủ kho vật tư

Các nhóm nghiệp vụ được mô phỏng bao gồm quản lý công việc tại ao nuôi, ghi nhận môi trường nước, hoạt động chăm sóc, sức khỏe vật nuôi, thu hoạch, cân theo mẻ, kiểm tra chất lượng và vật tư.

## 3. Công nghệ sử dụng

- **HTML5:** Xây dựng cấu trúc giao diện.
- **CSS3:** Thiết kế bố cục, màu sắc và giao diện thích ứng.
- **JavaScript:** Điều hướng màn hình, xử lý tương tác và mô phỏng trạng thái nghiệp vụ.
- **Mock Data:** Dữ liệu giả lập phục vụ trình diễn.

Các prototype có thể chạy trực tiếp trên trình duyệt mà không yêu cầu cài đặt backend hoặc cơ sở dữ liệu.

## 4. Cấu trúc thư mục

```text
NongNghiep-Mobile-Prototype/
├── TrongTrot/
│   ├── CongNhan.html
│   ├── ToTruong.html
│   ├── KySu.html
│   ├── QuanLyNongTruong.html
│   ├── DieuPhoiThuMua.html
│   ├── TaiXe.html
│   ├── QC.html
│   └── ThuKho.html
│
├── ThuySan/
│   ├── CongNhan.html
│   ├── ToTruong.html
│   ├── KySu.html
│   ├── QuanLyTrai.html
│   ├── TaiXe.html
│   ├── QC.html
│   └── ThuKhoVatTu.html
│
└── README.md
```

## 5. Hướng dẫn sử dụng

### Bước 1. Tải prototype

Trên GitHub, chọn **Code → Download ZIP**, sau đó giải nén vào thư mục trên máy tính.

### Bước 2. Chọn lĩnh vực

Truy cập thư mục:

- `TrongTrot/`: Prototype Mobile Trồng trọt.
- `ThuySan/`: Prototype Mobile Thủy sản.

### Bước 3. Mở giao diện

Mở tệp HTML tương ứng với vai trò muốn trải nghiệm bằng trình duyệt Google Chrome hoặc Microsoft Edge.

Ví dụ:

- `TrongTrot/CongNhan.html`: Giao diện Công nhân Trồng trọt.
- `TrongTrot/ToTruong.html`: Giao diện Tổ trưởng Trồng trọt.
- `ThuySan/KySu.html`: Giao diện Kỹ sư Thủy sản.

Không cần cài đặt Node.js hoặc khởi chạy máy chủ để xem giao diện cơ bản.

## 6. Các luồng nghiệp vụ tiêu biểu

### Trồng trọt

**Luồng 1: Quản lý công việc**

Phân công công việc → Thực hiện công việc → Ghi nhật ký → Xem xét kết quả.

**Luồng 2: Thu hoạch và kiểm tra chất lượng**

Tạo lô thu hoạch → Ghi nhận cân → Kiểm tra chất lượng → Ghi nhận trạng thái QC.

### Thủy sản

**Luồng 1: Theo dõi môi trường ao nuôi**

Ghi nhận chỉ số môi trường → Xem trạng thái/cảnh báo → Ghi nhận xử lý.

**Luồng 2: Thu hoạch thủy sản**

Ghi nhận đợt thu hoạch → Cân theo mẻ → Kiểm tra chất lượng.

Các luồng trên được thể hiện bằng những màn hình và tình huống giả lập trong phạm vi của từng prototype. Chúng không đại diện cho một giao dịch liên thông thực tế giữa các tệp HTML.

## 7. Giới hạn của phiên bản

Đây là phiên bản **mockup/prototype**, chưa phải ứng dụng triển khai thực tế.

- Không kết nối backend hoặc cơ sở dữ liệu production.
- Không thực hiện giao dịch nghiệp vụ thật.
- Không tích hợp trực tiếp với thiết bị cân, camera, GPS hoặc thiết bị đo.
- Không bảo đảm đồng bộ dữ liệu giữa các vai trò.
- Một số chức năng và kịch bản vẫn đang được tiếp tục hoàn thiện, kiểm tra.

Dữ liệu hiển thị chỉ phục vụ mục đích mô phỏng và trình diễn giao diện.

## 8. Mục đích sử dụng

Bộ prototype được sử dụng để:

- Minh họa kết quả nghiên cứu và thiết kế giao diện trong quá trình thực tập.
- Trình diễn các màn hình theo vai trò và quy trình nghiệp vụ tiêu biểu.
- Hỗ trợ xem xét, đánh giá và điều chỉnh thiết kế trước khi triển khai ứng dụng thực tế.

**Lưu ý:** Repository chứa mã nguồn prototype phục vụ báo cáo thực tập, không phải bản phát hành chính thức của hệ thống NongNghiep.