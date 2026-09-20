# Phân công nội dung Chapter 5

Thư mục chapters/ chứa nội dung từng mục của Chapter 5. Mỗi file .tex tương ứng với một mục trong sách. Khi được phân công mục nào, hãy sửa đúng file của mục đó và viết nội dung ngay bên dưới dòng \section{...} hoặc dưới comment TODO có sẵn.

## Bảng phân công

| Họ và tên | MSSV | Mục | Trang | File cần sửa |
|---|---:|---|---:|---|
| Trần Lương Anh | 20237298 | 5.1, 5.2 | 210-216 | ch05_01_introduction.tex, ch05_02_plausibility_mu0.tex |
| Hồ Xuân Bắc | 20237301 | 5.3 | 216-220 | ch05_03_hotelling_likelihood.tex |
| Nguyễn Xuân Cường | 20237307 | 5.4 | 220-224 | ch05_04_confidence_regions.tex |
| Nguyễn Minh Đức | 20237313 | 5.4 | 225-229 | ch05_04_confidence_regions.tex |
| Vũ Công Hiệp | 20237328 | 5.4 | 230-234 | ch05_04_confidence_regions.tex |
| Phạm Minh Hiếu | 20237331 | 5.5 | 234-238 | ch05_05_large_sample_inferences.tex |
| Nguyễn Bá Đức Huy | 20237345 | 5.6 | 239-243 | ch05_06_quality_control_charts.tex |
| Nguyễn Thị Thảo | 202419101 | 5.6 | 244-248 | ch05_06_quality_control_charts.tex |
| Trần Long Vũ | 20237409 | 5.6 | 249-251 | ch05_06_quality_control_charts.tex |

## Cách làm việc trong file .tex

- Không sửa main.tex nếu chỉ viết nội dung cho mục đã được phân công.
- Không sửa preamble.tex nếu không thay đổi style chung của tài liệu.
- Mỗi người viết đúng phần trang của mình trong file được giao.
- Với mục có nhiều người cùng làm, hãy thêm comment đánh dấu phần của mình trước khi viết, ví dụ:

    % BEGIN Nguyễn Xuân Cường - trang 220-224
    Nội dung ở đây...
    % END Nguyễn Xuân Cường - trang 220-224

## Build kiểm tra PDF

Từ thư mục gốc repo, chạy:

    xelatex -interaction=nonstopmode -file-line-error main.tex

Trong VS Code, có thể dùng extension LaTeX Workshop và build từ main.tex.
