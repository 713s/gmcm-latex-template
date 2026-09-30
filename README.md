# 数学建模 LaTeX 模板

**使用时一定注意检查封面图片，该模板是26年，二十三届，西交**

以 `main.tex` 为入口，使用 `gmcmthesis.cls` 排版。论文正文、姓名、学校和报名号已替换为占位内容。

## 编译

安装包含中文支持的 TeX Live 或 MiKTeX，使用 **XeLaTeX**：

```bash
xelatex -interaction=nonstopmode -halt-on-error main.tex
xelatex -interaction=nonstopmode -halt-on-error main.tex
```

也可以上传到 Overleaf，将编译器设为 XeLaTeX。模板不附带商业字体；类文件支持 Noto Serif CJK SC 与 ctex 默认字体回退。自行使用本地字体时请遵守字体授权。

## 使用

- 修改 `main.tex` 中标题、报名号、学校、成员和摘要等占位信息。
- 保留了行内公式、编号公式、多行公式、矩阵、分段函数和积分示例。
- 保留了图片、图题、交叉引用、普通三线表及 60 行虚构数据的跨页长表。
- `longtable` 直接放在正文中，不要外套 `table` 或 `resizebox`。示例包含续页表头和“续下页”页脚。
- `figures/` 的研究图件仅为排版示例，不能作为模板使用者的研究结果。发布前请替换为自己的图件。

## 图片格式与引用

| 格式 | 类型 | 放大是否失真 | LaTeX 支持 | 文件大小 | 推荐用途 |
|---|---|---:|---|---|---|
| **PDF** | vector | 不失真 | **原生支持，非常好** | 通常较小 | **论文作图首选** |
| PNG | raster | 会失真 | 原生支持 | 可能较大 | heatmap、照片、像素图 |
| SVG | vector | 不失真 | 非原生，需要转换 | 通常较小 | 网页、Inkscape 编辑、中间文件 |

PDF 中嵌入的位图仍受像素分辨率限制。文件大小取决于图件复杂度与压缩方式。

```tex
\begin{figure}[htbp]
  \centering
  \includegraphics[width=.8\linewidth]{figures/example.pdf}
  \caption{图片说明}
  \label{fig:example}
\end{figure}
参见图~\ref{fig:example}。
```

PDF 与 PNG 使用相同的引用命令。上述 `example.pdf` 是占位文件名；默认示例使用仓库中实际存在的 PNG。SVG 可先用 Inkscape 转换：

```bash
inkscape figures/example.svg --export-type=pdf --export-filename=figures/example.pdf
```

## 来源

`gmcmthesis.cls` 沿用当前项目的修改版本，其文件头指向 [zhanwen/MathModel](https://github.com/zhanwen/MathModel)。本仓库保留来源说明，不重新声明第三方类文件、封面图片或示例图片的许可。请按各素材原始授权使用；竞赛提交格式以当年官方要求为准。
