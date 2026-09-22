---
title: "For Looping Sederhana Python"
date: 2026-09-22T12:11:01+07:00
draft: false
toc: false
images:
tags:
  - untagged
---

Halo, *coder*! Kali ini kita bahas trik cepat bikin kode Python lebih bersih dan rapi pakai *List Comprehension*.

Biasanya, kalau kita mau bikin list angka kuadrat dari 1 sampai 5, kita nulis *for loop* kayak gini:

```python
angka = []
for i in range(1, 6):
  angka.append(i**2)

print(angka)  # Output: [1, 4, 9, 16, 25]
