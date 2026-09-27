# Slide LaTeX

Thư mục này chứa source Beamer cho slide thuyết trình, dùng template HUST đã copy từ `HUST_THEME_BEAMER___LATEX_BY_FRC`.

## Cấu trúc

```text
slides/
├── main.tex                 # File chính để build slide
├── beamerthemeHUST.sty      # Theme HUST đang được main.tex sử dụng
├── images/                  # Ảnh nền/logo blue của HUST theme
├── figures/                 # Hình minh họa riêng của nhóm nếu có
└── sections/                # Chia slide theo từng mục gốc của Chapter 5 và bài tập
```

## Sửa ở đâu

- Sửa nội dung từng phần trong `sections/*.tex`.
- Sửa tiêu đề, tên nhóm, thứ tự các phần trong `main.tex`.
- Thêm hình dùng riêng cho slide vào `figures/`.
- Không sửa `images/` nếu chỉ đang viết nội dung slide, vì đây là ảnh nền blue của theme.

## Build slide

Chạy từ thư mục `slides`:

```powershell
xelatex -interaction=nonstopmode -file-line-error main.tex
```

Trong VS Code, mở `slides/main.tex` rồi build bằng LaTeX Workshop.
