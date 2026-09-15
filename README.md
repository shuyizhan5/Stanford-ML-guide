# 美国量化实习指南

这是一个可直接部署到 GitHub Pages 的书籍主页。完整书籍保留为 PDF，避免将 200 多页内容逐页转成 Markdown。

## 发布前只需完成两项替换

1. 将你的原创 PDF 放入本目录，命名为 `book.pdf`。
2. 在 `index.html` 底部，将“小红书主页链接将在正式发布时补入”的文字替换为你的实际主页链接。

## 发布到 GitHub Pages

1. 在 GitHub 新建一个公开仓库，例如 `quant-internship-guide`。
2. 将本目录中的全部文件上传到仓库根目录。
3. 在仓库中打开 `Settings`，进入 `Pages`。
4. 在 `Build and deployment` 中选择 `Deploy from a branch`，选择 `main` 分支和 `/(root)` 文件夹，保存。
5. 等待发布完成。书籍主页地址会是：

   `https://YOUR_GITHUB_USERNAME.github.io/quant-internship-guide/`

   PDF 直链会是：

   `https://YOUR_GITHUB_USERNAME.github.io/quant-internship-guide/book.pdf`

如果 `book.pdf` 大于 100MB，不能直接放进 GitHub 仓库。请压缩 PDF，或将 PDF 作为 GitHub Release 附件上传，并把 `index.html` 中两处 `book.pdf` 改成该 Release 的下载链接。

## 文件说明

- `index.html`：书籍主页。
- `book.pdf`：待加入的完整 PDF。
- `changelog.html`：版本与更新记录。
- `LICENSE`：非商业署名共享许可。仅在你拥有书籍版权时使用。

请勿上传公司内部资料、受保密约束的面试题、客户信息或不具备公开传播权的内容。
