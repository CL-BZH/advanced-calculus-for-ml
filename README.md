# Advanced Calculus for Machine Learning

An advanced calculus book for readers who come from machine learning, in
the spirit of Loomis & Sternberg's *Advanced Calculus* and Hubbard &
Hubbard's *Vector Calculus, Linear Algebra, and Differential Forms*, with
one decision taken on the first page: the spaces in which calculus happens
are **affine spaces**.

A parameter of a model is a point; an update is a displacement. Both are
stored in the same arrays, and they are not the same kind of object. The
book keeps three such pairs apart from beginning to end:

| | | |
|---|---|---|
| points | vectors | `theta` vs. `theta_new - theta` |
| the differential (a covector) | the gradient (a vector) | what `backward()` computes vs. what the optimizer adds |
| the dual operator `Aᵀ` | the adjoint `A*` | no inner product needed vs. inner product needed |

and it applies two tests to every formula and algorithm: does it change
when the **origin** moves, and does it change when the **basis** changes?

**Status: work in progress.** Chapters 1 to 7 are drafted. The other
chapters contain their planned contents.

The PDF is rebuilt by GitHub Actions on every push to `main`:
[PDF of the latest push](https://github.com/CL-BZH/advanced-calculus-for-ml/releases/download/latest/Advanced_Calculus_for_Machine_Learning.pdf).
Tagged versions (`v*`) also get a release of their own.

## Contents

Each part adds one layer of structure.

**Part I — Spaces**

1. Affine Spaces *(drafted)*
2. Vector Spaces and Duality *(drafted)*
3. Inner Products and Euclidean Affine Spaces *(drafted)*
4. Norms, Topology and Banach Spaces *(drafted)*
5. Symmetric Operators and the SVD *(drafted)*

**Part II — Differential Calculus**

6. The Differential *(drafted)*
7. The Chain Rule and Automatic Differentiation *(drafted)*
8. Gradient, Hessian and Taylor's Formula
9. The Mean Value Inequality, Contractions and Newton's Method
10. The Inverse and Implicit Function Theorems
11. Constrained Optimization

**Part III — Manifolds**

12. Submanifolds of an Affine Space
13. Abstract Manifolds, Tangent and Cotangent Bundles
14. Riemannian Metrics and Optimization on Manifolds
15. Information Geometry and the Natural Gradient

**Part IV — Measure and Integration**

16. Measures
17. The Lebesgue Integral
18. Product Measures and the Fubini–Tonelli Theorem
19. *Lᵖ* Spaces
20. Change of Variables

**Part V — Differential Forms and Flows**

21. Multilinear Algebra
22. Differential Forms and the Exterior Derivative
23. Integration on Manifolds and Stokes' Theorem
24. Gradient, Curl and Divergence
25. Differential Equations and Flows

**Appendix** — A. Construction of Lebesgue Measure; B. Solutions to the
Exercises

## Repository layout

```
book/
  main.tex            main file
  chapters.tex        one \include per chapter
  preamble/           packages, macros, visual style
  chapters/           one directory per part, one file per chapter
  backmatter/         solutions to the exercises
  STYLE.md            environments, notation and writing conventions
notebooks/            one PyTorch notebook per chapter (CPU only)
```

## Building the book

A TeX Live installation with `latexmk` is enough.

```sh
cd book
make                                              # the whole book -> main.pdf
make chapter CH=chapters/01-spaces/01-affine-spaces   # one chapter -> chapter.pdf
make clean
```

## Notebooks

Each chapter has a companion notebook that checks its numerical claims
with assertions. They need only PyTorch and run on a CPU in a few seconds.

```sh
pip install -r notebooks/requirements.txt
jupyter notebook notebooks/01-affine-spaces.ipynb
```

## Conventions

Every result that is stated is proved; definitions and proofs are followed
by an explanation in words; machine learning examples are set in their own
boxes; every exercise has a complete solution at the end of the book. See
[`book/STYLE.md`](book/STYLE.md).

## Related

[Notes on Machine Learning](https://github.com/CL-BZH/ml-notes-book), whose
chapter on the geometry of the gradient was the starting point of this
book.

## License

MIT; see [`LICENSE`](LICENSE).
