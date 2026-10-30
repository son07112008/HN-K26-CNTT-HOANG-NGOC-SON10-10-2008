Phần 1: Báo cáo phân tích I/O (Luồng dữ liệu Ctrl+S đến tích xanh)
Input: Nhấn Ctrl+S trên trình soạn thảo; hệ điều hành ghi nhận thay đổi trực tiếp vào ổ cứng SSD cục bộ (Local Storage) để tối ưu tốc độ.

Process: Phần mềm Cloud chạy ngầm tự động quét thay đổi bằng cơ chế Delta Sync (chỉ chọn lọc phần code sửa đổi, bỏ qua thư mục node_modules).

Output: Gói dữ liệu nhỏ được truyền an toàn lên Cloud Server. Khi máy chủ xác nhận lưu trữ thành công, biểu tượng tích xanh hiển thị trên tệp.

Phần 2: Xử lý bẫy dữ liệu node_modules
Vấn đề: Thư mục chứa hàng vạn file nhỏ gây treo phần mềm và tràn dung lượng Cloud nếu bật Auto Sync.

Giải pháp: Đưa thư mục node_modules vào tệp cấu hình loại trừ (.gitignore hoặc cài đặt tính năng Exclude Folder trong phần mềm Cloud). Chỉ đồng bộ file quản lý cấu hình (package.json và package-lock.json), sau đó dùng lệnh npm install để tải lại thư viện khi cần.

Phần 3: Sơ đồ tổ chức thư mục Cloud chuẩn
Plaintext
  My-Cloud-Workspace/
  Code/                  # Mã nguồn dự án (đã loại trừ node_modules)
  Docs/                  # Tài liệu kỹ thuật, file đặc tả, README.md
  Assets/                # Tài nguyên tĩnh (hình ảnh, icons, media)