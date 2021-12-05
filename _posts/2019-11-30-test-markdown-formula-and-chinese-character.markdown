---
title: "Markdown 数学公式"
layout: post
date: 2014-09-20 00:00
tag:
- markdown
star: false
category: blog
author: jsyqrt
---

---

## Mathjax

---

Inline math \\( 1/x^{2} \\).

`Inline math \\( 1/x^{2} \\)`

Inline math $ 1/x^{2} $ with \$.

`Inline math $ 1/x^{2} $`

---

Block math.

\\[ \frac{1}{n^{2}} \\]

```text
Block math

\\[ \frac{1}{n^{2}} \\]
```

---

Block math with \$.

$$
\frac{1}{n^{2}}
$$

```text
Block math with \$

$$
\frac{1}{n^{2}}
$$
```

---

## Code block

---

```golang

func sum(a, b int) int {
    return a + b
}

```

---
