# BÁO CÁO BÀI TẬP: TÌM HIỂU VÀ THỰC HÀNH CÔNG CỤ KIỂM THỬ POSTMAN

## 📌 Thông Tin Sinh Viên
- **Họ và tên:** Nguyễn Đăng Hanh
- **Mã sinh viên:** 23010243
- **Lớp:** K17_CNTT_3
- **Nội dung:** Báo cáo thực hành công cụ Postman API Testing

---

## 📝 Giới Thiệu Bài Tập
Báo cáo này ghi lại quá trình tìm hiểu, cài đặt và thực hành các tính năng cốt lõi của công cụ **Postman** dùng trong kiểm thử API. Nội dung bao gồm việc làm quen với giao diện điều khiển, khởi tạo bộ sưu tập (Collection), gửi các yêu cầu HTTP (Requests), phân tích dữ liệu phản hồi (Response), cấu hình tham số nâng cao và xây dựng kịch bản kiểm thử tự động (Test Automation) cơ bản bằng JavaScript.

---

## Nội Dung Thực Hiện & Kết Quả Chi Tiết

### 1. Cài đặt và Thiết lập Môi trường
- Tải và cài đặt phiên bản Postman phù hợp với hệ điều hành.
- Đăng nhập tài khoản cá nhân và khởi tạo Không gian làm việc (**My Workspace**) để quản lý dự án.

> <img width="1919" height="1025" alt="image" src="https://github.com/user-attachments/assets/408df547-0ac9-44a1-bf91-cfd359c5e3c0" />


### 2. Khởi tạo Test Collection và Gửi API Request
- Tạo một thư mục lưu trữ tập trung các API mang tên: `Test Collection of APIs`.
- Sử dụng API công khai để thử nghiệm: `https://randomuser.me/api/`.
- Thực hiện gửi phương thức **GET Request** để yêu cầu máy chủ trả về thông tin người dùng ngẫu nhiên dưới định dạng JSON.
- **Kết quả phân tích:**
  - Dữ liệu hiển thị trực quan ở định dạng cấu trúc cây dễ đọc (**Pretty mode**).
  - Trạng thái phản hồi đạt mã chuẩn **200 OK**.
  - Thời gian phản hồi (Response Time) hiển thị chi tiết (tính bằng mili-giây).

><img width="1566" height="1023" alt="image" src="https://github.com/user-attachments/assets/eef401a7-3a36-4070-8558-e3dd6a2e2fc6" />


### 3. Tìm hiểu Thành phần cấu trúc Request nâng cao
Trong quá trình nghiên cứu, các khái niệm quan trọng sau của API đã được làm rõ trực tiếp trên Postman:
- **Query Parameters (Params):** Thiết lập các tham số lọc sau dấu `?` trên URL (ví dụ: `?beer_type=light`) giúp giới hạn hoặc định hình dữ liệu trả về theo nhu cầu.
- **Headers:** Quản lý các cặp Key-Value hệ thống tự tạo hoặc tự định nghĩa (như ngôn ngữ, định dạng Content-Type) để bổ sung thông tin cho gói tin gửi đi.
- **Authorization:** Tìm hiểu cơ chế xác thực quyền truy cập đối với các Private API (như API Key, Bearer Token, Basic Auth).
- **Body & Form Data:** Thực hành gửi dữ liệu phức tạp lên máy chủ bằng định dạng `raw (JSON)` ứng với các phương thức sửa đổi dữ liệu (POST, PUT, PATCH), cũng như cách đính kèm tệp tin đa phương tiện lên API qua tab `form-data`.

<img width="1553" height="1029" alt="image" src="https://github.com/user-attachments/assets/c9771ad1-3a9b-4b28-b4a0-dfab3f7f6296" />


### 4. Xây dựng Kịch bản Kiểm thử Tự động (Test Automation)
Sử dụng các đoạn mã JavaScript tích hợp sẵn (Snippets) trong tab **Tests** để tự động hóa việc thẩm định tính chính xác của phản hồi trả về từ API:
- Viết kịch bản kiểm tra mã trạng thái bắt buộc phải bằng 200:
  ```javascript
  pm.test("Status code is 200", function () {
      pm.response.to.have.status(200);
  });
