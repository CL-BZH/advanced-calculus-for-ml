# Style guide

The book's visual and pedagogical conventions, shared with the companion
book *Notes on Machine Learning*. All definitions are in
`preamble/style.tex`; chapters use only the environments listed here and
define no boxes of their own.

## Structure of a chapter

```latex
\begin{notechapter}
\chapter{Title}
\label{ch:slug}
\chaptersubtitle{One-line subtitle}

\begin{chapterintro}
  One paragraph of motivation from machine learning, then "You will learn"
  + itemize of goals.
  \prerequisites{chapters or topics the reader needs}
\end{chapterintro}

\section{...}   % explanation, definitions, results with proofs, examples

\begin{chaptersummary} itemize of the key results \end{chaptersummary}

\section*{Exercises}
\addcontentsline{toc}{section}{Exercises}
\begin{exercise} ... \hint{...} \end{exercise}
\end{notechapter}
```

Every exercise has a label `slug:exr:N` and ends with
`\solutionlink{slug:exr:N}`. Its solution goes in `backmatter/solutions.tex`,
in the section of its chapter, introduced by `\solution{slug:exr:N}` (which
links back to the statement).

Labels are prefixed with the chapter slug: `slug:sec:...`, `slug:thm:...`,
`slug:eq:...`, `slug:fig:...`. Cross-references use `\cref`.

A chapter that is not written yet contains only its title, subtitle and a
`chapterplan` box listing its planned contents.

## Environments

| Environment | Use | Look |
|---|---|---|
| `theorem`, `proposition`, `lemma`, `corollary` | results that are proved | blue left bar |
| `definition`, `assumption` | definitions | green left bar |
| `example` | worked examples with numbers | orange left bar |
| `remark` | side comments | unboxed |
| `intuition` | what a definition or a result says, in words | blue box titled "In words" |
| `keyidea` | the one thing to remember from a section | purple titled box |
| `pitfall` | common mistakes and misreadings | red titled box |
| `mlthread` | where the mathematics shows up in machine learning | teal titled box |
| `chapterintro`, `chaptersummary` | chapter frame | shaded / grey box |
| `chapterplan` | planned contents of an unwritten chapter | grey box |
| `exercise` (+ `\hint`, `\solutionlink{label}`) | exercises, numbered per chapter | plain |

Boxes take an optional title: `\begin{pitfall}[Zero counts]`.

## Notation

| Symbol | Macro | Meaning |
|---|---|---|
| $\mathcal A$, $\mathcal B$ | `\Aff`, `\Bff` | affine spaces (sets of points) |
| $V$, $W$ | | their directions (vector spaces of displacements) |
| $a, b, c, o$ | | points; $o$ is an origin |
| $u, v, w$ | | vectors |
| $a + v$, $b - a$ | | point plus vector; the vector from $a$ to $b$ |
| $x$, $\omega$, $\beta$, $\gamma$ | | coordinate arrays of $a$, $w$, $f(o)$, $g$ |
| $\vec f$ | `\lin{f}` | linear part of an affine map $f$ |
| $V^*$ | | dual space; its elements are covectors |
| $A^\top$ | `\dual{A}` | **dual operator** $W^*\to V^*$ (no inner product) |
| $A^*$ | `\adj{A}` | **adjoint** $W\to V$ (needs inner products) |
| $\mathrm d f_a$, $Df(a)$ | `\dd f_a` | differential at $a$ (a covector if $f$ is scalar) |
| $\nabla f(a)$ | | gradient: the vector representing $\mathrm d f_a$ for an inner product |

The transpose symbol is reserved for the dual operator and for the
transpose of a matrix; the star is reserved for the adjoint. In an
orthonormal basis the two have the same matrix, and the text says so each
time it uses the fact. Many references write $A^*$ (or $A'$, $A^t$,
${}^t\!A$) for the dual operator: when a result is taken from another
source, it is restated in the book's notation, and Chapter 2 gives the
translation table.

## Writing

- Explain before formalizing: motivation, then definition, then result and
  proof, then a worked example with numbers.
- Every result that is stated is proved; results that are only quoted are
  attributed to a reference.
- After a definition or a proof, say in words what it means (`intuition`).
- Three distinctions are never blurred: points and vectors; differential
  and gradient; dual operator and adjoint.
- Two tests are applied to formulas and algorithms: the origin test
  (Chapter 1) and the basis test (Chapter 2).
- Prose over bullet lists; lists only for genuinely parallel items.
- Figures are drawn in TikZ/pgfplots wherever a picture helps; data for
  plots are computed, not sketched by hand, when they are meant to be read
  quantitatively.
- LaTeX sources are wrapped at 80 columns.

## Notebooks

Each chapter has a companion notebook `notebooks/NN-slug.ipynb` (PyTorch,
CPU only, a few seconds to run) that checks the chapter's numerical claims
with assertions. Notebooks are committed with their outputs. The chapter
refers to its notebook with `\notebook{NN-slug.ipynb}`.
