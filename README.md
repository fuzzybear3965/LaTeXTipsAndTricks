# LaTeXTipsAndTricks
A repository of helpful Stackexchange posts and tips and tricks for working
with LaTeX documents and the various engines. I've had all sorts of issue
compiling figures and changing fonts. This is just me keeping track of the
solutions to various problems that I've had.


# Table of Contents
1. [Figures](#figures)
2. [Fonts](#fonts)

# Figures
## PGF/TikZ
### External library
1. Compile a `LateX` document containing references to (parts of) `TikzPicture`
environments when using the `external` library.

This is related to the problem of creating a plot with dual y-axes and a commond
legend. In that case, the recommended solution is to use `\label`s in the first
`axis` environment for each plot for which you want a legend entry. Then, in the
second `axis` environment, you refer back to those `\label`s using an
`\addlegendimage` command with `\ref`s hearkening back to the `\label`s in the
first axis (described in more detail in [this PGFPlots problem](#pgfplots-1)).

In order to get the legend to compile properly, however, the document needs to
be recompiled since the references to the `label`s will be initially undefined
when using the `external` library. The solution to this, currently, is to *not* use
`\usetikzlibrary{external}` but, instead, to use the version that comes with
PGFPlots, which is more recent. Thus,
```latex
\usepackage{pgfplots}
\usetikzlibrary{external}
\tikzexternalize
```
should become
```latex
\usepackage{pgfplots}
\usepgfplotslibrary{external}
\tikzexternalize
```
.

### PGFPlots
1. <a id="pgfplots-1"></a>

# Fonts
