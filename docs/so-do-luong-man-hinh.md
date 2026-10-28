# Sơ đồ luồng màn hình prototype

Sơ đồ tập trung vào chuyển màn hình, không khẳng định các vai tạo thành một ứng dụng backend thống nhất. Tên vai/tệp trong sơ đồ được đối chiếu với các HTML hiện có trong workspace.

## 1. Mobile Trồng trọt

```mermaid
flowchart TD
  Boot["Mở tệp HTML của vai"] --> Splash["Khởi động"] --> Tenant{"Đã cấu hình đơn vị?"}
  Tenant -- "Chưa" --> Setup["Thiết lập / chọn đơn vị"] --> Login["Đăng nhập demo"]
  Tenant -- "Đã có" --> Login
  Login --> Home["Trang chính"]

  Home --> Functions["Tất cả chức năng"]
  Home --> Queue["Hàng chờ"]
  Home --> Notifications["Thông báo / chi tiết"]
  Home --> Account["Tài khoản / trợ giúp / đăng xuất"]

  Functions --> Worker["Công nhân"]
  Worker --> WTasks["Việc hôm nay / chi tiết việc"]
  Worker --> WDiary["Ghi nhật ký / chụp ảnh / đã lưu"]
  Worker --> WPlots["Hồ sơ lô / bản đồ"]
  Worker --> WAttendance["Chấm công"]
  Worker --> WMaterials["Vật tư / yêu cầu trả"]

  Functions --> Leader["Tổ trưởng"]
  Leader --> LTasks["Việc của tổ / chi tiết việc"]
  Leader --> LHarvest["Lệnh thu hoạch / danh sách lô"]
  LHarvest --> LCreate["Tạo lô / chi tiết lô"] --> LWeigh["Cân / nhập lần cân"] --> LHandoff["Bàn giao / QR"]
  Leader --> LAttendance["Chấm công / quét QR"]

  Functions --> Engineer["Kỹ sư"]
  Engineer --> EPlots["Danh sách lô / bản đồ / chi tiết"]
  Engineer --> EDiary["Nhật ký / tạo / chi tiết / lịch sử"]
  Engineer --> EApproval["Duyệt nhật ký / kết quả"]
  Engineer --> EMaterials["Vật tư / yêu cầu trả / cách ly"]

  Functions --> Manager["Quản lý nông trường"]
  Manager --> MOps["Điều hành / công việc / tiến độ tổ"]
  Manager --> MPlots["Danh sách lô / bản đồ / chi tiết"]
  Manager --> MDiary["Nhật ký / duyệt / kết quả bước 2"]
  Manager --> MHarvest["Lệnh / lô thu hoạch / QR / hiệu chỉnh cân"]

  Functions --> Buyer["Điều phối thu mua"] --> Collection["Điểm gom"] --> Receive["Nhận lô"] --> Raw["Lô nguyên liệu / QR"]
  Functions --> Driver["Tài xế"] --> Trips["Chuyến của tôi"] --> TripDetail["Chi tiết chuyến"] --> TripReceive["Nhận lô"] --> TripComplete["Giao xong"]
  Functions --> QC["QC"] --> QCQueue["Hàng chờ QC"] --> QCForm["Phiếu QC"] --> QCDecision["Quyết định"]
  Functions --> Warehouse["Thủ kho"] --> WHHome["Kho thành phẩm"] --> WHAction{"Chọn màn kho"}
  WHAction --> Inbound["Nhập kho"]
  WHAction --> Move["Chuyển kho"]
  WHAction --> Outbound["Xuất kho"]
  WHAction --> Count["Kiểm kê"]
  WHAction --> Lookup["Tra cứu"]
```

### Nhóm tệp vai

| Vai | Tệp |
|---|---|
| Công nhân | `Mobile_TrongTrot/CongNhan.html` |
| Tổ trưởng | `Mobile_TrongTrot/ToTruong.html` |
| Kỹ sư | `Mobile_TrongTrot/KySu.html` |
| Quản lý nông trường | `Mobile_TrongTrot/QuanLyNongTruong.html` |
| Điều phối thu mua | `Mobile_TrongTrot/DieuPhoiThuMua.html` |
| Tài xế | `Mobile_TrongTrot/TaiXe.html` |
| QC | `Mobile_TrongTrot/QC.html` |
| Thủ kho | `Mobile_TrongTrot/ThuKho.html` |

Từng tệp đóng gói màn hình theo một vai và có bộ điều hướng/quyền riêng. “Tất cả chức năng” là danh mục trong tệp vai, không phải menu cấp phép từ một máy chủ.

## 2. Mobile Thủy sản

```mermaid
flowchart TD
  Open["Mở tệp HTML theo vai"] --> Splash["Khởi động mô phỏng"] --> Login["Đăng nhập demo"] --> Home["Trang chính / tác vụ nhanh"]
  Home --> Queue["Hàng chờ"]
  Home --> Notices["Thông báo / chi tiết"]
  Home --> Account["Tài khoản / đổi vai mô phỏng / đặt lại demo"]
  Home --> AI["Trợ lý VBDAgri: hội thoại/điều hướng mô phỏng"]

  Home --> Worker["Congnhan.html · Công nhân"]
  Worker --> WTasks["Việc hôm nay / chi tiết lệnh / lượt đi ao"]
  Worker --> WRecords["Đo nước / cho ăn / nhật ký / hao hụt / xử lý / dùng thuốc"]
  Worker --> WPond["Ao được giao / QR ao"]
  Worker --> WMaterials["Vật tư đang giữ / yêu cầu trả"]

  Home --> Leader["Totruong.html · Tổ trưởng"]
  Leader --> LWork["Việc của tổ / phân công"]
  Leader --> LPond["Thả giống / lấy mẫu / chuyển ao / cảnh báo"]
  Leader --> LHarvest["Đợt thu → lô thu → cân theo mẻ → bàn giao / QR"]
  Leader --> LDiary["Nhật ký / vật tư"]

  Home --> Engineer["Kysu.html · Kỹ sư"]
  Engineer --> EApprove["Duyệt nhật ký bước 1 / lịch sử"]
  Engineer --> EAlerts["Cảnh báo / xử lý / lệnh"]
  Engineer --> ETreatment["Phiếu điều trị / ngưng thuốc"]
  Engineer --> EProduction["Thả giống / chuyển ao / lấy mẫu / nhật ký / thu hoạch"]

  Home --> Manager["Quanlytrai.html · Quản lý trại"]
  Manager --> MApprove["Duyệt nhật ký bước 2"]
  Manager --> MPlan["Kế hoạch / tiến độ tổ / cảnh báo / ao-vụ / vụ chờ đóng / thu hoạch"]

  Home --> Driver["Taixe.html · Tài xế"]
  Driver --> Trips["Chuyến / chi tiết / lô trên chuyến"]
  Trips --> Scan["Quét QR lô mô phỏng"] --> Depart["Xác nhận xuất phát"] --> Track["Tuyến / GPS / nhiệt độ / độ tươi"] --> Arrive["Xác nhận đến nơi / theo dõi cân nhận"]

  Home --> QC["QC.html · QC"] --> QueueQC["Lô chờ QC / lô đủ điều kiện"] --> Inspection["Phiếu QC / lịch sử nuôi / lab"] --> Gate["Chốt cổng QC"] --> QCResult["Kết quả / lô HOLD"]

  Home --> Warehouse["Thukhovattu.html · Thủ kho vật tư"] --> WHRequests["Yêu cầu trả / phiếu xuất"] --> Receive["Xác nhận thực nhận"] --> WHHistory["Lịch sử / quét QR / tồn theo lô / vật tư khóa"]
```

### Tệp vai

`Mobile_ThuySan/Congnhan.html`, `Totruong.html`, `Kysu.html`, `Quanlytrai.html`, `Taixe.html`, `QC.html` và `Thukhovattu.html`.

Các trang nghiệp vụ mở từ Trang chính/tác vụ nhanh; thanh điều hướng chung dẫn tới Trang chính, Hàng chờ, Thông báo và Tài khoản. Trợ lý hội thoại là mô phỏng, không kết nối AI/micro thật.

## 3. Ghi chú khi dùng sơ đồ

- Màn hình dùng chung về mặt tên (ví dụ đăng nhập, hàng chờ) không có nghĩa dùng chung tài khoản, backend hoặc giao dịch.
- Luồng Trồng trọt giữa các vai là sơ đồ màn hình tham khảo; mỗi vai lưu mock state riêng.
- Thủy sản dùng cùng khóa localStorage giữa các tệp, nhưng chỉ những collection được cập nhật/đọc tương ứng mới phản ánh dữ liệu qua vai. Các đường bàn giao chưa nối được ghi rõ trong [sơ đồ nghiệp vụ](so-do-luong-nghiep-vu.md).
- Tài liệu AgriOS liên quan trong `D:\Project\agrios-main\agrios-main` được dùng để đối chiếu phạm vi dự kiến; danh mục màn hình ở đây lấy từ prototype hiện có, không lấy chức năng chỉ xuất hiện trong SOW/SRS.
