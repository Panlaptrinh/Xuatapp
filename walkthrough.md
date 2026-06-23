# Hướng dẫn nhận file APK qua GitHub

Dự án hiện tại của bạn đã được cấu hình thành công thành một ứng dụng Android hoàn chỉnh tại thư mục `D:\Xuatapp\pwa-app`. Đi kèm với đó là cấu hình **GitHub Actions** giúp tự động hóa quá trình build ra file `.apk` mà không cần cài đặt thêm phần mềm nào trên máy tính.

Dưới đây là các bước để bạn đưa dự án lên GitHub và nhận về file `.apk`.

## Bước 1: Tạo kho lưu trữ (Repository) trên GitHub
1. Đăng nhập vào [GitHub](https://github.com/).
2. Bấm vào nút **New** (hoặc dấu `+` góc trên bên phải) để tạo một Repository mới.
3. Đặt tên (ví dụ: `task-app-android`), có thể để trạng thái là **Private** (Riêng tư).
4. **Không** đánh dấu vào các mục khởi tạo README hay .gitignore. Bấm **Create repository**.

## Bước 2: Đẩy dự án của bạn lên GitHub
Trên máy tính của bạn, mở **Terminal** (hoặc PowerShell/Command Prompt), di chuyển vào thư mục `D:\Xuatapp\pwa-app` và chạy lần lượt các lệnh sau (nhớ thay `<link_github_cua_ban>` bằng đường dẫn repository bạn vừa tạo ở Bước 1, ví dụ `https://github.com/TenCuaBan/task-app-android.git`):

```bash
cd D:\Xuatapp\pwa-app
git init
git add .
git commit -m "Init Android project"
git branch -M main
git remote add origin <link_github_cua_ban>
git push -u origin main
```

## Bước 3: Tải file APK về
1. Sau khi chạy xong lệnh `git push`, quay lại trang GitHub của bạn và chuyển sang tab **Actions**.
2. Bạn sẽ thấy một tiến trình có tên **"Init Android project"** đang chạy màu vàng (hoạt động này diễn ra từ 2-4 phút).
3. Đợi tiến trình chuyển sang màu xanh (Tích xanh thành công), hãy bấm vào nó.
4. Cuộn xuống phần **Artifacts** ở dưới cùng. Tại đây bạn sẽ thấy một file tên là `app-debug`. Nhấp vào đó để tải xuống!

> [!TIP]
> File tải về sẽ nằm dưới dạng `.zip`, bạn giải nén ra sẽ thấy file `app-debug.apk` ở bên trong. Hãy chép nó vào điện thoại Android của bạn và cài đặt!

## Xử lý khi bạn cập nhật code sau này
Nếu sau này bạn muốn chỉnh sửa giao diện hay chức năng (bằng cách chỉnh sửa file `src/App.tsx`), bạn chỉ cần chạy lại 2 lệnh sau ở thư mục `pwa-app` để đẩy lên GitHub, hệ thống sẽ tự động xuất APK mới:
```bash
git add .
git commit -m "Cap nhat chuc nang"
git push
```
Mỗi lần như vậy, bạn lại vào tab Actions tải APK mới về máy nhé!
