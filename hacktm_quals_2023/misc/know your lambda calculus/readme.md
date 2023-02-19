# Description

~~~
Let's have some fun with Lambda Calculus!

nc 34.141.16.87 60000

---
Added example:

Question:
s = λa b. a (a b)
t = λa b. a (a a)

Solution:
'(λv0 v1 f. f v0 v1)', '(λv0 f. f v0)', '(holder)', '(λv0 v1. v0)', '(holder)', '(λv0 v1. v0)', '(holder)', '(λi0 i1. (λx y. x))', '(λi0 i1. (λx y. y))'
---

---
How the interpreter reduces terms:

(λa b. a (λc. a a (b b c)) a) (λp0 p1. p1 p0 p0) (λp2 p3 p4 p5 p6. p3 p1) (λq q q q q q q q x y. y) (λq q q q q q q x y. x) e f g h i
(λb. (λp0 p1. p1 p0 p0) (λc. (λp0 p1. p1 p0 p0) (λp0 p1. p1 p0 p0) (b b c)) λp0 p1. p1 p0 p0) (λp2 p3 p4 p5 p6. p3 p1) (λq q q q q q q q x y. y) (λq q q q q q q x y. x) e f g h i
(λp0 p2. p2 p0 p0) (λc. (λp0 p2. p2 p0 p0) (λp0 p2. p2 p0 p0) ((λp2 p3 p4 p5 p6. p3 p1) (λp2 p3 p4 p5 p6. p3 p1) c)) (λp0 p2. p2 p0 p0) (λq q q q q q q q x y. y) (λq q q q q q q x y. x) e f g h i
(λp2. p2 (λc. (λp0 p2. p2 p0 p0) (λp0 p2. p2 p0 p0) ((λp2 p3 p4 p5 p6. p3 p1) (λp2 p3 p4 p5 p6. p3 p1) c)) λc. (λp0 p2. p2 p0 p0) (λp0 p2. p2 p0 p0) ((λp2 p3 p4 p5 p6. p3 p1) (λp2 p3 p4 p5 p6. p3 p1) c)) (λp0 p2. p2 p0 p0) (λq q q q q q q q x y. y) (λq q q q q q q x y. x) e f g h i
(λp0 p2. p2 p0 p0) (λc. (λp0 p2. p2 p0 p0) (λp0 p2. p2 p0 p0) ((λp2 p3 p4 p5 p6. p3 p1) (λp2 p3 p4 p5 p6. p3 p1) c)) (λc. (λp0 p2. p2 p0 p0) (λp0 p2. p2 p0 p0) ((λp2 p3 p4 p5 p6. p3 p1) (λp2 p3 p4 p5 p6. p3 p1) c)) (λq q q q q q q q x y. y) (λq q q q q q q x y. x) e f g h i
(λp2. p2 (λc. (λp0 p2. p2 p0 p0) (λp0 p2. p2 p0 p0) ((λp2 p3 p4 p5 p6. p3 p1) (λp2 p3 p4 p5 p6. p3 p1) c)) λc. (λp0 p2. p2 p0 p0) (λp0 p2. p2 p0 p0) ((λp2 p3 p4 p5 p6. p3 p1) (λp2 p3 p4 p5 p6. p3 p1) c)) (λc. (λp0 p2. p2 p0 p0) (λp0 p2. p2 p0 p0) ((λp2 p3 p4 p5 p6. p3 p1) (λp2 p3 p4 p5 p6. p3 p1) c)) (λq q q q q q q q x y. y) (λq q q q q q q x y. x) e f g h i
(λc. (λp0 p2. p2 p0 p0) (λp0 p2. p2 p0 p0) ((λp2 p3 p4 p5 p6. p3 p1) (λp2 p3 p4 p5 p6. p3 p1) c)) (λc. (λp0 p2. p2 p0 p0) (λp0 p2. p2 p0 p0) ((λp2 p3 p4 p5 p6. p3 p1) (λp2 p3 p4 p5 p6. p3 p1) c)) (λc. (λp0 p2. p2 p0 p0) (λp0 p2. p2 p0 p0) ((λp2 p3 p4 p5 p6. p3 p1) (λp2 p3 p4 p5 p6. p3 p1) c)) (λq q q q q q q q x y. y) (λq q q q q q q x y. x) e f g h i
(λp0 p2. p2 p0 p0) (λp0 p2. p2 p0 p0) ((λp2 p3 p4 p5 p6. p3 p1) (λp2 p3 p4 p5 p6. p3 p1) λc. (λp0 p2. p2 p0 p0) (λp0 p2. p2 p0 p0) ((λp2 p3 p4 p5 p6. p3 p1) (λp2 p3 p4 p5 p6. p3 p1) c)) (λc. (λp0 p2. p2 p0 p0) (λp0 p2. p2 p0 p0) ((λp2 p3 p4 p5 p6. p3 p1) (λp2 p3 p4 p5 p6. p3 p1) c)) (λq q q q q q q q x y. y) (λq q q q q q q x y. x) e f g h i
(λp2. p2 (λp0 p2. p2 p0 p0) λp0 p2. p2 p0 p0) ((λp2 p3 p4 p5 p6. p3 p1) (λp2 p3 p4 p5 p6. p3 p1) λc. (λp0 p2. p2 p0 p0) (λp0 p2. p2 p0 p0) ((λp2 p3 p4 p5 p6. p3 p1) (λp2 p3 p4 p5 p6. p3 p1) c)) (λc. (λp0 p2. p2 p0 p0) (λp0 p2. p2 p0 p0) ((λp2 p3 p4 p5 p6. p3 p1) (λp2 p3 p4 p5 p6. p3 p1) c)) (λq q q q q q q q x y. y) (λq q q q q q q x y. x) e f g h i
(λp2 p3 p4 p5 p6. p3 p1) (λp2 p3 p4 p5 p6. p3 p1) (λc. (λp0 p2. p2 p0 p0) (λp0 p2. p2 p0 p0) ((λp2 p3 p4 p5 p6. p3 p1) (λp2 p3 p4 p5 p6. p3 p1) c)) (λp0 p2. p2 p0 p0) (λp0 p2. p2 p0 p0) (λc. (λp0 p2. p2 p0 p0) (λp0 p2. p2 p0 p0) ((λp2 p3 p4 p5 p6. p3 p1) (λp2 p3 p4 p5 p6. p3 p1) c)) (λq q q q q q q q x y. y) (λq q q q q q q x y. x) e f g h i
(λp3 p4 p5 p6. p3 p1) (λc. (λp0 p2. p2 p0 p0) (λp0 p2. p2 p0 p0) ((λp2 p3 p4 p5 p6. p3 p1) (λp2 p3 p4 p5 p6. p3 p1) c)) (λp0 p2. p2 p0 p0) (λp0 p2. p2 p0 p0) (λc. (λp0 p2. p2 p0 p0) (λp0 p2. p2 p0 p0) ((λp2 p3 p4 p5 p6. p3 p1) (λp2 p3 p4 p5 p6. p3 p1) c)) (λq q q q q q q q x y. y) (λq q q q q q q x y. x) e f g h i
(λp4 p5 p6. (λc. (λp0 p2. p2 p0 p0) (λp0 p2. p2 p0 p0) ((λp2 p3 p4 p5 p6. p3 p1) (λp2 p3 p4 p5 p6. p3 p1) c)) p1) (λp0 p2. p2 p0 p0) (λp0 p2. p2 p0 p0) (λc. (λp0 p2. p2 p0 p0) (λp0 p2. p2 p0 p0) ((λp2 p3 p4 p5 p6. p3 p1) (λp2 p3 p4 p5 p6. p3 p1) c)) (λq q q q q q q q x y. y) (λq q q q q q q x y. x) e f g h i
(λp5 p6. (λc. (λp0 p2. p2 p0 p0) (λp0 p2. p2 p0 p0) ((λp2 p3 p4 p5 p6. p3 p1) (λp2 p3 p4 p5 p6. p3 p1) c)) p1) (λp0 p2. p2 p0 p0) (λc. (λp0 p2. p2 p0 p0) (λp0 p2. p2 p0 p0) ((λp2 p3 p4 p5 p6. p3 p1) (λp2 p3 p4 p5 p6. p3 p1) c)) (λq q q q q q q q x y. y) (λq q q q q q q x y. x) e f g h i
(λp6. (λc. (λp0 p2. p2 p0 p0) (λp0 p2. p2 p0 p0) ((λp2 p3 p4 p5 p6. p3 p1) (λp2 p3 p4 p5 p6. p3 p1) c)) p1) (λc. (λp0 p2. p2 p0 p0) (λp0 p2. p2 p0 p0) ((λp2 p3 p4 p5 p6. p3 p1) (λp2 p3 p4 p5 p6. p3 p1) c)) (λq q q q q q q q x y. y) (λq q q q q q q x y. x) e f g h i
(λc. (λp0 p2. p2 p0 p0) (λp0 p2. p2 p0 p0) ((λp2 p3 p4 p5 p6. p3 p1) (λp2 p3 p4 p5 p6. p3 p1) c)) p1 (λq q q q q q q q x y. y) (λq q q q q q q x y. x) e f g h i
(λp0 p2. p2 p0 p0) (λp0 p2. p2 p0 p0) ((λp2 p3 p4 p5 p6. p3 p1) (λp2 p3 p4 p5 p6. p3 p1) p1) (λq q q q q q q q x y. y) (λq q q q q q q x y. x) e f g h i
(λp2. p2 (λp0 p2. p2 p0 p0) λp0 p2. p2 p0 p0) ((λp2 p3 p4 p5 p6. p3 p1) (λp2 p3 p4 p5 p6. p3 p1) p1) (λq q q q q q q q x y. y) (λq q q q q q q x y. x) e f g h i
(λp2 p3 p4 p5 p6. p3 p1) (λp2 p3 p4 p5 p6. p3 p1) p1 (λp0 p2. p2 p0 p0) (λp0 p2. p2 p0 p0) (λq q q q q q q q x y. y) (λq q q q q q q x y. x) e f g h i
(λp3 p4 p5 p6. p3 p1) p1 (λp0 p2. p2 p0 p0) (λp0 p2. p2 p0 p0) (λq q q q q q q q x y. y) (λq q q q q q q x y. x) e f g h i
(λp4 p5 p6. p1 p1) (λp0 p2. p2 p0 p0) (λp0 p2. p2 p0 p0) (λq q q q q q q q x y. y) (λq q q q q q q x y. x) e f g h i
(λp5 p6. p1 p1) (λp0 p2. p2 p0 p0) (λq q q q q q q q x y. y) (λq q q q q q q x y. x) e f g h i
(λp6. p1 p1) (λq q q q q q q q x y. y) (λq q q q q q q x y. x) e f g h i
p1 p1 (λq q q q q q q x y. x) e f g h i
---
~~~
