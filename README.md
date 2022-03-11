# The issue

This repository demonstrates a strange behavior of `LaTeX`. It contains two
`.tex` files: `pic.tex` and `main.tex`. `pic.tex` is a document which uses the
`standalone` class to only render TikZ which produces a pdf with a line.
`main.tex` includes `pic.pdf` via `\includegraphics{pic.pdf}` four times. Once
it is included on the top level of its `document` environment and the other
three times within a `node` of a `tikzpicture` environment: one time as
`\node[draw, dashed] {\includegraphics{pic.pdf}}`, one time as `\node[draw,
dashed] {\mbox{\includegraphics{pic.pdf}}}` and one time as `\node[draw,
dashed] {\parbox{...}{\includegraphics{pic.pdf}}}`. For the latter three the
TikZ style of the node changes the behavior or the included *pdf file*; i.e.,
we obtain:

![illustration of the issue]{./main.png}

We provide a [`Makefile`]{./Makefile} to reproduce the issue. `pdflatex` needs
to be available. Also we require the packages `tikz` and `graphicx`.
