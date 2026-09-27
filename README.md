# Applied Multivariate Vietnamese

Repo này dùng để quản lý bản dịch Chapter 5 và source LaTeX cho slide thuyết trình.

## Cấu trúc thư mục

```text
.
├── translation/          # Bản dịch Chapter 5 dạng LaTeX
│   ├── main.tex
│   ├── preamble.tex
│   ├── chapters/
│   └── figures/
├── slides/               # Slide thuyết trình dạng Beamer/LaTeX
│   ├── main.tex
│   ├── beamerthemeHUST.sty
│   ├── images/           # Ảnh nền/logo blue của HUST theme
│   ├── figures/          # Hình minh họa riêng của nhóm
│   └── sections/         # Chia slide theo mục gốc của Chapter 5 và bài tập
├── .github/workflows/    # CI kiểm tra build LaTeX
└── README.md
```

## Sửa ở đâu

- Sửa nội dung bản dịch trong `translation/chapters/*.tex`.
- Sửa cấu hình bản dịch trong `translation/preamble.tex`.
- Sửa nội dung slide trong `slides/sections/*.tex`.
- Sửa cấu hình/tựa đề/thứ tự slide trong `slides/main.tex`.
- Thêm hình cho bản dịch vào `translation/figures/`.
- Thêm hình riêng cho slide vào `slides/figures/`.

## Build bản dịch

Project dùng `fontspec`, vì vậy phải build bằng XeLaTeX hoặc LuaLaTeX. Không dùng `pdflatex`.

```powershell
cd translation
xelatex -interaction=nonstopmode -file-line-error main.tex
```

Nếu có mục lục, citation hoặc cross-reference, chạy lệnh build từ 2 lần trở lên để LaTeX cập nhật số trang và tham chiếu.

## Build slide

```powershell
cd slides
xelatex -interaction=nonstopmode -file-line-error main.tex
```

## CI/CD kiểm tra biên dịch

GitHub Actions tại `.github/workflows/latex-build.yml` sẽ build cả hai project:

- `translation/main.tex` cho bản dịch.
- `slides/main.tex` cho slide.

Workflow chạy khi có Pull Request vào `main`, khi push lên `main` các file LaTeX/hình ảnh, hoặc khi chạy thủ công bằng `workflow_dispatch`.

## Quy trình làm việc với Git

- Không commit trực tiếp vào `main`.
- Mỗi thay đổi nên tạo một nhánh riêng, ví dụ `feature/ch05-02-content` hoặc `feature/slides-outline`.
- Sau khi sửa xong, push nhánh lên GitHub và tạo Pull Request vào `main`.
- Chủ repo review Pull Request trước khi merge.
- Không commit các file build tự sinh như `.aux`, `.log`, `.synctex.gz`, `.pdf`; các file này đã được cấu hình trong `.gitignore`.
