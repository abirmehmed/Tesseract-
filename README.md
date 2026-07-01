# Tesseract-

<img width="1859" height="906" alt="image" src="https://github.com/user-attachments/assets/e3e88034-fc61-48c6-94fd-477717c8e58e" />


<img width="1859" height="906" alt="image" src="https://github.com/user-attachments/assets/53d89b3b-db55-42cc-ac3d-e077032ce0e3" />

## Formal definition

A tesseract (also called an **8-cell** or **hypercube of dimension 4**) is the 4-dimensional analogue of the cube. The cleanest way to define it:

**As a set of points:**
$$T = \{(x_1, x_2, x_3, x_4) \in \mathbb{R}^4 : -1 \le x_i \le 1 \text{ for all } i\}$$

Its boundary — the "surface" — consists of every point where at least one coordinate hits ±1.

**As a Cartesian product**, it's just four copies of an interval, multiplied together:
$$T = [-1,1] \times [-1,1] \times [-1,1] \times [-1,1]$$

Compare: a square is $[-1,1]^2$, a cube is $[-1,1]^3$, a tesseract is $[-1,1]^4$. Same object, one more factor each time.

## The counting formulas (why your code's numbers weren't arbitrary)

For an *n*-dimensional hypercube:

| Element | Formula | Tesseract (n=4) |
|---|---|---|
| Vertices | $2^n$ | 16 |
| Edges | $n \cdot 2^{n-1}$ | 32 |
| 2D square faces | $\binom{n}{2} \cdot 2^{n-2}$ | 24 |
| 3D cells | $2n$ | 8 |
| Rotation planes | $\binom{n}{2}$ | 6 |

Every number you saw in your app's readout — "16 vertices, 32 edges" — comes directly out of these formulas, not from just counting a picture.

**Schläfli symbol:** the tesseract is written $\{4,3,3\}$ — read right to left, it means "cubes {4,3} arranged 3 around each edge." Compare the cube's symbol $\{4,3\}$ ("squares {4} arranged 3 around each vertex"). Each entry describes one more layer of "what surrounds what," and it's the formal way mathematicians classify all the regular polytopes in any dimension.

---

## Now, the things that are genuinely surprising

**1. In 3D, every rotation has a fixed axis. In 4D, most rotations have *no* fixed line at all.**

This is the big one, and it's the actual mathematical reason your project's six independent sliders work the way they do. Spin a real object in 3D and there's always a line — the axis — that doesn't move. In 4D, a *generic* rotation has only a single fixed point (the origin) and **decomposes into two completely independent rotations happening in two separate planes at the same time**, each possibly at a different speed. This is called an **isoclinic rotation** when the two speeds are equal, and it's connected to why quaternions (used in almost all 3D game engines and robotics for smooth rotation) are secretly 4-dimensional objects. When you had XY and XW both spinning at once in your app, you weren't looking at two hacks bolted together — you were looking at exactly what a real 4D rotation actually *is*, decomposed into its two natural pieces.

**2. A tesseract falling through our 3D world wouldn't look like a cube — it'd look like a cube that grows, twists, and shrinks.**

Just like a sphere passing through a 2D plane (think Flatland) shows up as a point that grows into a circle and shrinks back to a point, a tesseract passing through our 3D space intersects it as a *sequence of solids* — starting as a point, growing into an oddly-morphing polyhedron, sometimes looking cube-like, sometimes not, before shrinking away. If a 4D being existed and passed a tesseract through our universe, we'd never see the whole thing at once — only ever a strange, shifting 3D cross-section.

**3. There's a famous painting of a tesseract, and it's by Salvador Dalí.**

*Corpus Hypercubus* (1954) shows Christ crucified on an unfolded tesseract — the 4D equivalent of unfolding a cardboard box flat (a cube unfolds into a cross of 6 squares; a tesseract "unfolds" into a cross made of 8 cubes, called its *net*). Dalí was deliberately using 4D geometry as a religious/mystical symbol. It's one of the only pieces of mainstream fine art built entirely around a hypercube.

**4. The word "tesseract" is only about 135 years old.**

It was coined in 1888 by Charles Howard Hinton, a mathematician (and, colorfully, a bigamist who fled England after the scandal broke) who spent years trying to train people to *intuitively visualize* 4D objects using colored cubes and memorization drills. Some of his ideas about visualizing higher dimensions are still referenced in recreational math today.

**5. A cube has 11 different ways to unfold flat. A tesseract has 261.**

If you've ever unfolded a cardboard box, you've made one of a cube's 11 possible "nets." A tesseract, unfolded into 3D space (the way a cube unfolds into 2D), has **261 distinct nets** — this was only proven by exhaustive computer search, not by hand, because the number is too large to check by intuition alone.

**6. The tesseract's "opposite" shape is the 16-cell — and it's hiding inside your own code.**

Every regular polytope has a *dual* — swap vertices and cells, and you get a related shape. The tesseract's dual is the **16-cell** (8 vertices, 32 edges, 24 faces, 16 tetrahedral cells) — it's like how a cube's dual is an octahedron. Interestingly, the 16-cell's vertices are exactly the 8 points you get by taking $(\pm1,0,0,0)$ and permuting which axis holds the nonzero value — meaning it's *built from the same 4 axes* your rotation code already uses, just connected differently.

# Glome 

<img width="1853" height="897" alt="image" src="https://github.com/user-attachments/assets/486ba8dd-cb38-4f25-b037-d516387c3dc0" />

<img width="1853" height="897" alt="image" src="https://github.com/user-attachments/assets/101be41a-c000-4145-bd06-1c0d36a5dc0b" />

