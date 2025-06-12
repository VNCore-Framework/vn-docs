## Hướng Dẫn Cài Đặt FiveM Server với Artifact và txAdmin

### Bước 1: Tạo Thư Mục Server và Tải Artifact

- Tạo một thư mục mới trên Desktop, đặt tên tùy ý.
- Truy cập trang tải [FiveM Artifacts](https://runtime.fivem.net/artifacts/fivem/build_server_windows/) để tải bản Artifact mới nhất được đề xuất.
- Giải nén file Artifact vào thư mục vừa tạo.

<div align="center">
  <img src="/img/builds.png" align="center" height="200" />
</div>

### Bước 2: Khởi Động FXServer và txAdmin

- Mở thư mục vừa giải nén, nhấp đúp vào `FXServer.exe` để chạy.
- Khi server khởi động, trình duyệt sẽ tự động mở trang quản lý txAdmin.
- txAdmin đã được tích hợp sẵn trong Artifact, chỉ cần chạy FXServer là txAdmin sẽ khởi động.


### Bước 3: Thiết Lập Tài Khoản và Đăng Nhập

- Liên kết tài khoản FiveM (thường sẽ tự động).
- Đặt mật khẩu quản trị khi được yêu cầu.
- Làm theo các bước hướng dẫn trên giao diện txAdmin.
<div align="center">
    <img src="/img/txadmin.png" align="center" height="500" />
</div>

### Bước 4: Chọn Template và Lưu Trữ Dữ Liệu

- Chọn "📥 Remote URL Template" rồi điền URL 

```plaintext
https://raw.githubusercontent.com/VNCore-Framework/txAdminRecipe/refs/heads/main/vncore.yaml
```

<div align="center">
  <img src="/img/url.png" align="center" height="500" />
</div>
- Chọn thư mục để lưu dữ liệu server (nên dùng đường dẫn txAdmin đề xuất).
- Kéo xuống cuối trang và nhấn "Run Recipe Deployer".
- Nhấn "Next" để tiếp tục.

### Bước 5: Tạo và Nhập Keymaster Key

- Truy cập [Keymaster](https://keymaster.fivem.net/) để tạo key mới.
- Điền thông tin chính xác khi tạo key.
> **Lưu ý:** Keymaster chỉ yêu cầu địa chỉ IP lần đầu tiên, sau đó key có thể dùng cho bất kỳ IP nào.
- Dán key vào ô được yêu cầu trên txAdmin.

### Bước 6: Cài Đặt và Khởi Động Server

- Nhấn "Run Recipe" để bắt đầu cài đặt.
- Đợi quá trình cài đặt hoàn tất, bạn sẽ thấy màn hình thông báo thành công.
> **Cảnh báo:** Nếu gặp lỗi, hãy tham gia Discord chính thức của QBCore và đăng bài trong mục fivem-support.
> **Lưu ý:** Hãy để quá trình cài đặt Yarn hoàn tất ở lần khởi động đầu tiên.

### Bước 7: Cấu Hình Quyền Quản Trị

- Sau khi hoàn tất, nên tham khảo file `setting-permissions.md` để cấu hình quyền trong `server.cfg` cho các tài khoản quản trị.

---
