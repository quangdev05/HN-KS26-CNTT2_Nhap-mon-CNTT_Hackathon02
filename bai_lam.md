# BÀI LÀM – HACKATHON 02

- **Mã đề:** 08
- **Họ tên:** Phạm Duy Quang
- **Lớp:** HN-KS26-CNTT2
- **Link repository:** https://github.com/quangdev05/HN-KS26-CNTT2_Nhap-mon-CNTT_Hackathon02
- **Hệ điều hành (Windows/macOS):** Windows

## 4.2. Thao tác máy tính cơ bản bằng CLI

### Các lệnh đã chạy

```shell
pwd
gci -Force
mv "quy_trinh_thu_am.txt" docs
mkdir backup
cp "data/lich_thu_thang_8.xlsx" backup
rm *.tmp
cd logs
gci
cd ..
gci -R -Force

```

### Kết quả liệt kê toàn bộ dự án (Windows: Get-ChildItem -Recurse -Force; macOS: ls -aR)

```text
Directory: D:\Thi-KTMon\starter-kit\phong-thu-am-website


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----        11/11/2026     13:37                backup
d-----        11/11/2026     13:33                data
d-----        11/11/2026     13:35                docs
d-----        11/11/2026     13:32                envidence
d-----        11/11/2026     13:33                logs
d-----        11/11/2026     13:31                web
-a----        11/03/2026     07:08             74 .env
-a----        11/11/2026     13:39           2709 bai_lam.md


    Directory: D:\Thi-KTMon\starter-kit\phong-thu-am-website\backup


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----        11/03/2026     07:08           6136 lich_thu_thang_8.xlsx


    Directory: D:\Thi-KTMon\starter-kit\phong-thu-am-website\data


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----        11/03/2026     07:08           6136 lich_thu_thang_8.xlsx


    Directory: D:\Thi-KTMon\starter-kit\phong-thu-am-website\docs


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----        11/03/2026     07:08            157 quy_trinh_thu_am.txt


    Directory: D:\Thi-KTMon\starter-kit\phong-thu-am-website\logs


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----        11/03/2026     07:08            992 studio.log


    Directory: D:\Thi-KTMon\starter-kit\phong-thu-am-website\web


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----        11/11/2026     13:31                images
-a----        11/03/2026     07:08            586 app.js
-a----        11/03/2026     07:08            514 index.html
-a----        11/03/2026     07:08            460 style.css


    Directory: D:\Thi-KTMon\starter-kit\phong-thu-am-website\web\images


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----        11/03/2026     07:08           3097 logo-soundlab.png

```

## 4.3. Lọc log truy cập website

### a) Lệnh lọc các dòng status=500

```shell
sls "status=500" logs/studio.log > logs/loi_500.txt

```

### 2 dòng đầu tiên trong logs/loi_500.txt

```text
logs\studio.log:8:2026-08-28 08:25:34 POST /api/dat-lich status=500
logs\studio.log:11:2026-08-28 08:34:07 POST /api/thanh-toan status=500

```

### b) Lệnh đếm số dòng status=404 và kết quả

```shell
sls "status=404" logs/studio.log | Measure

```

```text
Count    : 4

```

## 4.4. Chạy script tong_hop (.ps1 hoặc .sh)

### Lệnh chạy (Windows: nếu dùng Phụ lục 2 thì ghi cả 2 lệnh)

```shell
./tong_hop.ps1

```

### Nội dung file logs/tong_hop.txt

```text
=== BAO CAO SU CO WEBSITE ===

2026-08-28 08:16:01 GET /tin-tuc status=404
2026-08-28 08:47:51 GET /san-pham-cu status=404
2026-08-28 08:58:24 GET /images/phong-thu-2.jpg status=404
2026-08-28 09:00:35 GET /images/phong-thu-2.jpg status=404




Count    : 6
Average  :
Sum      :
Maximum  :
Minimum  :
Property :





```

## 4.5. README.md và bảo vệ thông tin bí mật

> README.md, .gitignore và .env.example được chấm trực tiếp trên file ở gốc dự án. Đánh dấu `[x]` vào các mục đã làm để tự kiểm tra.

- [x] README.md: Heading 1, mô tả có **in đậm** và _in nghiêng_, bảng, code block, task list, blockquote
- [x] .gitignore có dòng `.env` (tên file đúng, không có đuôi .txt)
- [x] .env.example có đủ tên biến, giá trị để trống (tên file đúng, không có đuôi .txt)

## 4.6. Kiểm tra trang web bằng DevTools (F12) và báo cáo lỗi

### Bảng lỗi

| STT | Tab DevTools phát hiện lỗi | Tên file hoặc thông báo lỗi                                                                                 | Cách khắc phục                                                                                                 |
| --- | -------------------------- | ----------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------- |
| 1   | ERR_FILE_NOT_FOUND         | GET file:///D:/Thi-KTMon/starter-kit/phong-thu-am-website/web/images/logo-sound.png net::ERR_FILE_NOT_FOUND | Cập nhật lại tên trong đoạn code từ <img src="images/logo-sound.png" thành <img src="images/logo-soundlab.png" |
| 2   | Uncaught ReferenceError    | app.js:18 Uncaught ReferenceError: hienThiGoiThuAm is not defined (anonymous) @ app js:18                   |                                                                                                                | Đổi tên "hienThiGoiThuAm();" thành "hienThiGoiThu();" |

> Ảnh chụp màn hình lưu trong thư mục `evidence/` (network.png, console.png).

### Báo cáo lỗi gửi trưởng nhóm

- **Context:** Kiểm tra website SoundLab trong thư mục web, mở DevTools bằng F12.
- **Expected:** Logo hiển thị và bảng giá sân được tải lên trang.
- **Actual:** Console báo "Uncaught ReferenceError: hienThiGoiThuAm is not defined"
- **Log:** app.js:18 Uncaught ReferenceError: hienThiGoiThuAm is not defined (anonymous) @ app.js:18

### Câu tìm kiếm Google

```text
site:stackoverflow.com "Uncaught ReferenceError: "

```

## 4.7. Excel

> Phần Excel được chấm trực tiếp trên file `data/lich_thu_thang_8.xlsx`, không cần ghi vào đây.
