# Applied Multivariate Vietnamese

Repo này dùng để soạn thảo tài liệu LaTeX cho Chapter 5: Inferences About a Mean Vector.

## Cấu trúc thư mục

```text
.
├── main.tex
├── preamble.tex
├── chapters/
│   ├── ch05_01_introduction.tex
│   ├── ch05_02_plausibility_mu0.tex
│   ├── ch05_03_hotelling_likelihood.tex
│   ├── ch05_04_confidence_regions.tex
│   ├── ch05_05_large_sample_inferences.tex
│   └── ch05_06_quality_control_charts.tex
└── figures/
```

## Sửa ở đâu

- `main.tex`: file chính để build PDF. File này quyết định thứ tự chương, mục và các file được nạp vào tài liệu.
- `preamble.tex`: cấu hình chung của tài liệu, gồm font, kích thước trang, header/footer, định dạng tiêu đề, bảng, hình và lệnh toán.
- `chapters/*.tex`: nội dung từng mục. Khi sửa nội dung, ưu tiên sửa trong file tương ứng với mục đang làm.
- `figures/`: lưu hình ảnh bên ngoài, ví dụ `.png`, `.jpg`, `.pdf` hoặc `.eps` nếu tài liệu cần chèn hình.

## Mapping nội dung Chapter 5

- `chapters/ch05_01_introduction.tex`: mục 5.1 Introduction.
- `chapters/ch05_02_plausibility_mu0.tex`: mục 5.2 The Plausibility of mu0 as a Value for a Normal Population Mean.
- `chapters/ch05_03_hotelling_likelihood.tex`: mục 5.3 Hotelling's T2 and Likelihood Ratio Tests.
- `chapters/ch05_04_confidence_regions.tex`: mục 5.4 Confidence Regions and Simultaneous Comparisons of Component Means.
- `chapters/ch05_05_large_sample_inferences.tex`: mục 5.5 Large Sample Inferences about a Population Mean Vector.
- `chapters/ch05_06_quality_control_charts.tex`: mục 5.6 Multivariate Quality Control Charts.

## Cách build PDF

Project dùng `fontspec`, vì vậy phải build bằng XeLaTeX hoặc LuaLaTeX. Không dùng `pdflatex`.

### Build bằng VS Code

1. Cài MiKTeX hoặc TeX Live.
2. Cài extension VS Code `LaTeX Workshop`.
3. Mở thư mục repo trong VS Code.
4. Mở `main.tex`.
5. Build bằng `Ctrl + Alt + B`.
6. Xem PDF bằng `Ctrl + Alt + V`.

### Build bằng terminal

```powershell
xelatex -interaction=nonstopmode -file-line-error main.tex
```

Nếu sau này có mục lục, citation hoặc cross-reference, hãy chạy lệnh build từ 2 lần trở lên để LaTeX cập nhật số trang và tham chiếu.

## CI/CD kiểm tra biên dịch

Repo có GitHub Actions tại `.github/workflows/latex-build.yml`.

CI tự chạy khi có Pull Request vào `main`, khi push các file `.tex`/`figures`, hoặc khi chạy thủ công bằng `workflow_dispatch`. Workflow sẽ:

- Build `main.tex` bằng XeLaTeX thông qua `latexmk`.
- Kiểm tra chắc chắn `main.pdf` được tạo.
- Quét `main.log` và fail nếu có lỗi LaTeX nghiêm trọng, lỗi công thức, undefined reference hoặc `Overfull \hbox`.
- Upload file PDF đã biên dịch thành artifact `main-pdf` để tải về kiểm tra.

Nếu CI fail, hãy mở log của job `Compile main.tex` trên GitHub Actions để xem dòng lỗi cụ thể.

## Quy trình làm việc với Git

- Không commit trực tiếp vào `main`.
- Mỗi thay đổi nên tạo một nhánh riêng, ví dụ `feature/ch05-02-content`.
- Sau khi sửa xong, push nhánh lên GitHub và tạo Pull Request vào `main`.
- Chủ repo review Pull Request trước khi merge.
- Không commit các file build tự sinh như `.aux`, `.log`, `.synctex.gz`, `.pdf`; các file này đã được cấu hình trong `.gitignore`.

Ví dụ workflow:

```powershell
git checkout -b feature/ch05-02-content
git add chapters/ch05_02_plausibility_mu0.tex
git commit -m "Add section 5.2 draft"
git push -u origin feature/ch05-02-content
```
