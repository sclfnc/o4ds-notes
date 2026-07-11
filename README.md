# Optimization for Data Science: Lecture Notes

Typeset lecture notes for **Optimization for Data Science**, University of Pisa,
academic year 2024/25. The notes cover optimization theory and algorithms:
convexity, gradient methods, nonsmooth optimization, duality, and constrained
algorithms, with a closing appendix of worked exercises.

> ⚠️ **Disclaimer.** Derived from the *Optimization for Data Science* course
> materials (Academic Year 2024/2025), MSc in Data Science & Business
> Informatics, University of Pisa.
>
> These notes are open educational content created by a student. They are **not
> an academic source** and may contain inaccuracies. You may freely share,
> modify, and reuse this material for educational and non-commercial purposes
> with appropriate attribution. The content is my personal interpretation of the
> professor's course materials and should not replace official teaching
> resources. I assume no responsibility for any errors or misinterpretations.
>
> These notes were produced with an **AI-in-the-middle** workflow: a first human
> pass, then **Claude Code** to support formulation, understanding, and
> rewriting, followed by a final human review.
>
> If you find errors, have suggestions, or spot unintentionally included
> copyrighted material (which I will promptly remove on notification), contact me
> at `sclfnc@proton.me`.

## Layout

- `main.tex`: entry point, in the folder root; identical across the whole
  notes collection (it only loads the shared preamble and the course file).
- `src/housestyle.tex`, shared house style: geometry, colors, section and ToC
  formatting, running heads, and the math environments (theorem, definition, …).
- `src/common-preamble.tex`: the shared package set, identical across courses.
- `src/course.tex`, everything specific to this course: title metadata, math
  macros, the `exercise` box, `hyperref`/`cleveref`, the bibliography resource,
  and the `\input{sec/...}` list.
- `sec/_NN_*.tex`: section files (the body of the notes), pulled in by `course.tex`.
- `sec/_10_appendix_exercises.tex`: worked exercises appendix.
- `references.bib`: bibliography (biblatex / Biber, numeric style).
- `o4ds-notes.pdf`: the compiled notes, in the folder root.
- No images and no `img/` folder: the notes carry no diagrams, only a few
  `booktabs` tables (comparison and complexity tables), typeset inline.

## Build

The notes use `biblatex` with the Biber backend and `cleveref` (which needs a
final pass for cross-references). Build from the folder root:

```bash
latexmk main.tex
```

`latexmk` runs pdflatex and Biber as many times as needed. All output lands in
the folder root: the compiled PDF as `o4ds-notes.pdf`, and the LaTeX auxiliaries
(`.aux`, `.log`, `.toc`, `.bcf`, `.bbl`, …) alongside it, all git-ignored via
`.gitignore`. A `.latexmkrc` in the folder sets this up (it renames the output
via `$jobname`). To do it by hand instead:

```bash
pdflatex -jobname=o4ds-notes main && biber o4ds-notes && pdflatex -jobname=o4ds-notes main && pdflatex -jobname=o4ds-notes main
```

Requires a standard TeX Live installation. Alternatively, upload the folder to
[Overleaf](https://www.overleaf.com) (New Project → Upload Project), set
`main.tex` as the main document, and compile.

## Credits

Written by **Francesco Secoli**, revised with the help of
[Claude Code](https://claude.com/claude-code): the course slides and lectures
were transcribed and refined into LaTeX, then reworked into standalone notes.
Based on the *Optimization for Data Science* course (a.y. 2024/25), University of
Pisa. Contributions welcome: open an issue or a pull request.

## Contents

The notes are nine sections plus a worked-exercises appendix, in reading order:

| # | Section | Topics |
|---|---------|--------|
| 1 | Foundations | Problem formulation, reformulations, existence of optima, multi-objective optimization |
| 2 | Linear algebra and quadratic forms | Norms, eigenvalues, spectral decomposition, matrix definiteness |
| 3 | Univariate optimization | Lipschitz continuity, golden-ratio and dichotomic search, Newton's method |
| 4 | Unconstrained optimality and convexity | Gradients, Hessians, optimality conditions, strong convexity |
| 5 | Gradient methods for quadratics | Steepest descent, conjugate gradient, preconditioning |
| 6 | Smooth unconstrained optimization | Line search, quasi-Newton, trust region, Nesterov acceleration |
| 7 | Nonsmooth unconstrained optimization | Subgradients, bundle methods; Lasso, SVM, SVR |
| 8 | Constrained optimality and duality | KKT conditions, Lagrangian duality, conic programs |
| 9 | Constrained optimization algorithms | Active set, projected gradient, Frank–Wolfe, interior point |
| A | Exercises | Appendix of solved problems |
