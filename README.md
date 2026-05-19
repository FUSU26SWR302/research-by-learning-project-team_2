# Hệ thống Quản lý Sự kiện & Hỗ trợ AI (University Event Management System)

Dự án phần mềm quản lý và điều phối hoạt động sự kiện tích hợp Trí tuệ nhân tạo, giúp số hóa toàn bộ quy trình từ khâu lập kế hoạch đến vận hành thực tế.

## 1. Thành viên nhóm

| STT | Họ và Tên | Vai trò chính trong dự án | Phân công công việc |
|---|---|---|---|
| 1 | **Trần Xuân Thuận** | Project Lead | Thiết kế kiến trúc hệ thống, phát triển Core API, tích hợp dịch vụ AI (RAG, Recommendation). |
| 2 | **Nguyễn Nhật Linh** | Frontend Developer | Phát triển giao diện Web/Mobile, tối ưu hóa UI/UX, tích hợp QR Scanner. |
| 3 | **Khưu Xuân Nhân** | Business Analyst / QA | Đặc tả yêu cầu hệ thống (SRS), phân tích Use Case, viết kịch bản kiểm thử (Test cases). |
| 4 | **Dương Phú Hoàng Tuấn** |BackEnd Developer | Thiết lập cơ sở dữ liệu, quản lý phân quyền hệ thống. |
| 5 | **Nguyễn Khoa Hiệp** | BackEnd Developer | Thiết lập cơ sở dữ liệu, quản lý phân quyền hệ thống. |


## 2. Tổng quan Dự án

### 2.1. Phân hệ Nghiệp vụ cốt lõi (Business Scope)
* **Quy trình phê duyệt khép kín:** Số hóa luồng xét duyệt sự kiện và đặt địa điểm (Venue Booking) giữa Ban quản lý CLB và Nhà trường.
* **Vận hành & Điểm danh:** Đăng ký sự kiện, cấp phát vé QR, kiểm soát Check-in/Check-out thời gian thực nhằm chống gian lận chuyên cần.
* **Quản trị & Kỷ luật:** Tính toán điểm hoạt động câu lạc bộ, xử lý vi phạm, quản lý phản hồi và báo cáo thống kê đa chiều.

### 2.2. Hàm lượng Nghiên cứu Khoa học & Công nghệ (Research Depth)
* **Hệ thống Gợi ý (Smart Recommendation):** Ứng dụng thuật toán Lọc cộng tác (Collaborative Filtering) dựa trên Độ tương đồng Cosine (Cosine Similarity) để gợi ý sự kiện phù hợp với lịch sử và sở thích của sinh viên.
* **Kiến trúc Trợ lý ảo (RAG Framework):** Tích hợp AI Assistant sử dụng Retrieval-Augmented Generation để truy xuất chính xác cẩm nang và quy chế nội bộ, giảm thiểu tình trạng AI sinh thông tin ảo (Hallucination).
* **Kiểm soát Truy cập Đa vai trò (Multi-role RBAC):** Nghiên cứu giải pháp cấp quyền cho phép một người dùng giữ nhiều vai trò (ví dụ: vừa là Sinh viên, vừa là Club Manager) và chuyển đổi không gian làm việc (Context Switch) không cần đăng nhập lại.
* **Xử lý Xung đột Lịch trình:** Thuật toán phát hiện giao thoa thời gian (Schedule Conflict Detection) cảnh báo sinh viên nếu sự kiện đăng ký trùng với lịch học hoặc sự kiện khác.

## 3. Quản lý Tiến độ Công việc (Jira)

Toàn bộ các task của dự án được quản lý theo mô hình Agile/Scrum và phân chia theo từng tuần (Sprint).
* **Đường dẫn Jira Board:** `https://tranxuanthuan20.atlassian.net/?continue=https%3A%2F%2Ftranxuanthuan20.atlassian.net%2Fwelcome%2Fsoftware%3FprojectId%3D10001&atlOrigin=eyJpIjoiZjNjZWZhNDgxMmY1NGEwN2FmMjdkNzI3NDg2ODcxMDciLCJwIjoiamlyYS1zb2Z0d2FyZSJ9`
* **Quy trình hoạt động:** Mỗi task đều được gắn (assign) cho từng thành viên với các trạng thái rõ ràng (To Do -> In Progress -> Review -> Done).

## 4. Thiết kế Giao diện & Kiến trúc Front-end

* **Không gian thiết kế UI/UX (Figma):** `https://www.figma.com/design/gKB9Izxw86T9KxhbzT1EVz/SWP391?node-id=0-1&t=d7vWbb4HlaOTdpKm-1`
* **Cấu trúc thư mục Front-end:**
  ```text
  frontend/
  ├── public/              # Tài nguyên tĩnh, logo, icon
  ├── src/
  │   ├── components/      # UI component dùng chung (Button, Modal, Table...)
  │   ├── views/           # Các màn hình chính chia theo Role (Guest, Student, Admin, University...)
  │   ├── services/        # Cấu hình gọi API, kết nối dịch vụ AI
  │   ├── store/           # Quản lý State của ứng dụng (Redux/Zustand hoặc Pinia)
  │   └── utils/           # Các hàm hỗ trợ định dạng ngày tháng
  └── package.json
