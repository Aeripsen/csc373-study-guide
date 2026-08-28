# CSC373 study site

Eleven pages covering the whole of CSC373 (Algorithm Design, Analysis and Complexity), built around
the structure of the actual exam paper rather than the order of the lectures.

Live at **https://aeripsen.github.io/csc373-study-guide/**

Or open `index.html` locally. No build step, no server, no internet connection needed.

## Why it is organised this way

The December 2024 final has seven questions, one per unit, in a fixed order, worth 90 marks over three
hours. That structure has been stable across papers, so every page here answers three questions about
its unit: what the exam question looks like, why the technique works, and the exact thing you write on
the paper.

The front page carries the mark split and a recommended order of attack. The two mechanical questions
(flow by hand, and LP standard form plus dual) are 20 marks with nothing to invent, and doing them
first clears the 40% pass floor before you meet anything that needs an original idea.

## Pages

| File | What is on it |
| --- | --- |
| `index.html` | Exam blueprint, the mark split, and routing by how much time you have left |
| `templates.html` | The seven answer skeletons, word for word, with a time budget. The page to drill |
| `divide-conquer.html` | Counting inversions, master theorem, closest pair, Karatsuba |
| `greedy.html` | Interval scheduling, minimising lateness, and the exchange argument in full |
| `dp.html` | Array, Bellman equation, bottom up fill, traceback, pseudo-polynomial time |
| `flow.html` | Residual networks, Ford Fulkerson, max flow min cut, reading a min cut |
| `flow-apps.html` | Bipartite matching, the four layer modelling pattern, image segmentation |
| `lp.html` | Standard form, duality, the absolute value and min max modelling tricks |
| `complexity.html` | Certificates and certifiers, reductions, NP completeness proofs |
| `drill.html` | Eleven past paper questions with full model answers |
| `cheatsheet.html` | The finished aid sheet: every formula, skeleton and trap, ready to copy by hand |

Shared stylesheet: `style.css`.

## Maths

Formulas are typeset with **KaTeX 0.16.11, vendored into `katex/`** (CSS, JS, the auto-render
extension and 21 woff2 fonts, about 600 KB). Nothing is fetched from a CDN, so the pages render
offline and cannot break when someone else's server does.

Delimiters are `$ ... $` inline and `$$ ... $$` for display. Auto-render is configured to **ignore
`<pre>` and `<code>`**, because pseudocode is code and not maths: it stays monospace on purpose, and
only real mathematical statements are typeset. Roughly 800 formulas across the eleven pages.

`cheatsheet.html` is the exception to "study material": it is written to be the finished aid sheet,
complete enough to copy by hand and carry into the exam with nothing else. It also has a print
stylesheet.

## Animations

Fifteen interactive pieces, all vanilla JavaScript drawing inline SVG. Each one exists to make a
specific mechanism visible, not for decoration.

- **Merge and count** shows why taking an element from the right half discovers a whole block of
  inversions at once.
- **Master theorem recursion tree** has sliders for a, b and the exponent of f(n), and shows which
  level of the tree dominates. That is the entire content of the three cases.
- **Closest pair** builds the delta strip and shows where the constant 11 comes from.
- **Interval scheduling** steps through earliest finish time first.
- **Wrong greedy rules** shows verified counterexamples to earliest start, shortest interval and
  fewest conflicts.
- **Exchange argument** animates swapping greedy's choice into an optimal solution.
- **DP table fill** fills a row left to right with dependency arrows, then traces back to recover the
  actual choices.
- **Ford Fulkerson** runs on a network where the last augmenting path uses a backward edge, with the
  residual drawn underneath, then reads the min cut off it.
- **Bipartite matching** builds the flow network in four steps.
- **Constraint to edge map** shows which network edge enforces which sentence of a word problem.
- **LP geometry** slides the objective and shows the optimum landing on a vertex.
- **Standard form and dual** steps through a real conversion one move at a time.
- **Reduction direction** shows what collapses when the arrow is reversed.
- **One graph, three readings** shows that S is independent exactly when the complement is a vertex
  cover and exactly when S is a clique in the complement graph.
- **Time budget** lays the seven questions across 180 minutes and marks where the pass floor is
  cleared under each ordering.

## Checks that were run

- All 11 pages start with `<!doctype html>` (without it, quirks mode stops `td` inheriting `color`).
- Every formula on every page renders: 805 of them, zero KaTeX errors, checked by loading each
  page in headless Chrome and counting `.katex-error` nodes.
- Zero external requests. No CDN, no web fonts, no images. Works offline from a copy.
- No em dashes or en dashes, as literal characters or as HTML entities.
- All internal links and cross page anchors resolve.
- Every script block parses, and every button and slider was driven against a DOM shim with no throws.
- The animation arithmetic was verified against brute force: the DP table matches an exhaustive
  search, the greedy schedule matches the true optimum, the Ford Fulkerson run satisfies conservation
  and capacity and produces a cut matching the flow value, the greedy counterexamples were found by
  search and their optimal sets checked disjoint, and the master theorem panel's case classification
  agrees with its bar directions across all 108 slider combinations.

## Sources

Written from the course's own slides, tutorials, assignments and past papers, so the notation and
method match what is taught: `c[j]` style arrays, `f_in(v)` and `f_out(v)` for flow, `X <=_P Y` for
polynomial time reduction, and the master theorem stated with `c = log_b(a)`.

No course material is reproduced here. No lecture slides, no handouts, no assignment or exam PDFs, no
official solution sets. Past paper questions are paraphrased only far enough to identify them, and
every worked answer is written from scratch.
