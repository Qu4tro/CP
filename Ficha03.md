Ficha 3
=====================

#### 1. Prove analiticamente a *lei da troca* (28): `[<f, g>, <h, k>] = <[f, h], [g, k]>`.

**R:**

    x = [<f, g>, <h, k>]
    ≡ Universal-+ (17)
    x · i1 = <f, g>
    x · i2 = <h, k>
    ≡ Universal-× (6)
    π1 . (x . i1) = f
    π2 . (x . i1) = g
    π1 . (x . i2) = h
    π2 . (x . i2) = k
    ≡ Assoc-comp (2)
    (π1 . x) . i1 = f
    (π2 . x) . i1 = g
    (π1 . x) . i2 = h
    (π2 . x) . i2 = k
    ≡ Universal-+ (17)
    π1 . x = [f, h]
    π2 . x = [g, k]
    ≡ Universal-× (6)
    x = <[f, h], [g, k]>


#### 2. Considere a função `undistl = [i1 × id, i2 × id]`.

    * Identifique o isomorfismo que ela testemunha, desenhando o diagrama respectivo.

**R:**

(A × C) + (B × C) ≅ (A + B) × C


![Diagram of undistl isomorphism](/images/undistl_iso.png)

* Recorra à lei da troca para re-escrever undistl sob a forma de um split.

        [i1 × id, i2 × id]
        ≡ Def-× (11)
        [<i1 · π1, id · π2>, <i2 · π1, id · π2>]
        ≡ Lei da troca (28)
        <[i1 · π1, i2 · π1], [id · π2, id · π2]>
        ≡ Natural-id (1)
        <[i1 · π1, i2 · π1], [π2, π2]>
        ≡ Def-+ (22)
        <π1 + π1, [π2, π2]>

* Demonstre a seguinte propriedade `π1 · undistl = π1 + π1`

        π1 · undistl = π1 + π1
        ≡ Def-undistl
        π1 · <π1 + π1, [π2, π2]> = π1 + π1
        ≡ Cancelamento-× (7)
        π1 + π1 = π1 + π1

* Derive a definição *pointwise* de undistl.

        undistl = [i1 × id, i2 × id]
        ≡ Universal-+
        undistl · i1 = i1 × id
        undistl · i2 = i2 × id
        ≡ Igualdade extensional (71)
        undistl · i1 (Xa, Yc) = i1 × id (Xa, Yc)
        undistl · i2 (Zb, Yc) = i2 × id (Zb, Yc)
        ≡ Def-comp (72)
        undistl (i1 (Xa, Yc)) = i1 × id (Xa, Yc)
        undistl (i2 (Zb, Yc)) = i2 × id (Zb, Yc)
        ≡ Def-× (77)
        undistl (i1 (Xa, Yc)) = (i1 Xa, id Yc)
        undistl (i2 (Zb, Yc)) = (i2 Xa, id Yc)
        ≡ Def-id (73)
        undistl (i1 (Xa, Yc)) = (i1 Xa, Yc)
        undistl (i2 (Zb, Yc)) = (i2 Xa, Yc)

#### 3. Mostre que `[k, k] = k` onde k é uma função constante (Uma função cujo resultado é sempre o mesmo, qualquer que seja o argumento).

    [k, k] = k
    ≡ Natural-const (3)
    [k · i1, k · i2] = k
    ≡ Fusão-+ (20)
    k · [i1, i2] = k
    ≡ Reflexão-+ (19)
    k · id = k
    ≡ Natural-id (1)
    k  = k


#### 4. Recorra à lei Eq-+ (entre várias outras) para mostrar que a equivalência das seguintes definições da função factorial:

    fac 0 = 1
    fac (n + 1) = (n + 1) * (fac n)

    fac · [0, succ] = [1, mul · <succ, fac>]

onde

    succ n = n + 1
    mul (a, b) = a * b


**R:**

    fac · [0, succ] = [1, mul · <succ, fac>]
    ≡ Fusão-+ (20)
    [fac · 0, fac · succ] = [1, mul · <succ, fac>]
    ≡ Eq-+ (27)
    fac · 0 = 1
    fac · succ = mul · <succ, fac>
    ≡ Igualdade-extensional (71)
    (fac · 0) n = 1 n
    (fac · succ) n = (mul · <succ, fac>) n
    ≡ Def-comp (72)
    fac (0 n) = 1 n
    fac (succ n) = mul (<succ, fac> n)
    ≡ Def-const (74)
    fac 0 = 1
    fac (succ n) = mul (<succ, fac> n)
    ≡ Def-split (76)
    fac 0 = 1
    fac (succ n) = mul (succ n, fac n)
    ≡ Def-succ
    fac 0 = 1
    fac (n + 1) = mul (n + 1, fac n)
    ≡ Def-succ
    fac 0 = 1
    fac (n + 1) = (n + 1) * (fac n)

    
#### 5. No contexto da questão anterior, considera a função `in = [0, succ]` que exprime a forma como os números naturais são gerados a partir do número 0.

Sabendo que o tipo 1 coincide com o tipo () em Haskell e é habitado por um único elemento, também designado por (), calcule a inversa de in.

    out 0 = i1 ()
    out (n + 1) = i2 n

resolvendo em ordem a out a equação `out · in = id` e introduzindo variáveis. (Poderá deste cálculo inferir que in e out são isomorfismos? Justifique.)

**R:**

    out · in = id
    ≡ Def-in
    out · [0, succ] = id
    ≡ Fusão-+ (20)
    [out · 0, out · succ] = id
    ≡ Reflexão-+ (19)
    [out · 0, out · succ] = [i1, i2]
    ≡ Eq-+ (27)
    out · 0  = i1
    out · succ = i2
    ≡ Igualdade-extensional (71)
    (out · 0) () = i1 ()
    (out · succ) n = i2 n
    ≡ Def-comp (72)
    out (0 ()) = i1 ()
    out (succ n) = i2 n
    ≡ Def-const (74)
    out 0 = i1 ()
    out (succ n) = i2 n
    ≡ Def-succ
    out 0 = i1 () 
    out (n + 1) = i2 n
    
    
#### 6. Demonstre a seguinte lei da fusão deste combinador condicional:


    (p → f, g) · h    = (p · h) → (f · h, g · h)

**R:**

    (p → f, g) · h    = (p · h) → (f · h, g · h)
    ≡ Def-Condicional de McCarthy (54)
    ([f, g] · p?) · h = (p · h) → (f · h, g · h)
    ≡ Assoc-comp (2)
    [f, g] · (p? · h) = (p · h) → (f · h, g · h)
    ≡ Natural-guarda (53)
    [f, g] · ((h + h) · (p · h)?) = (p · h) → (f · h, g · h)
    ≡ Assoc-comp (2)
    ([f, g] · (h + h)) · (p · h)? = (p · h) → (f · h, g · h)
    ≡ Absorção-+
    [f · h, g · h] · (p · h)? = (p · h) → (f · h, g · h)
    ≡ Def-Condicional de McCarthy (54)
    (p · h) → (f · h, g · h) = (p · h) → (f · h, g · h)

#### 7. Sabendo que as igualdades

    p → k, k = k 
    (p? + p?) · p? = (i1 + i2) · p?

se verificam, demonstre as seguintes propriedades do mesmo combinador:

    <(p → f, h), (p → g, i)> = p → <f, g>, <h, i>
    <f, (p → g, h)> = p → <f, g>, <f, h>
    p → (p → a, b), (p → c, d) = p → a, d

**R:** 

    <(p → f, h), (p → g, i)> = p → <f, g>, <h, i>
    ≡ Def-Condicional de McCarthy (54)
    <(p → f, h), (p → g, i)> = [<f, g>, <h, i>]·p?
    ≡ Lei da troca (28)
    <(p → f, h), (p → g, i)> = <[f, h], [g, i]>·p?
    ≡ Fusão-× (9)
    <(p → f, h), (p → g, i)> = <[f, h]·p?, [g, i]·p?>
    ≡ Def-Condicional de McCarthy (54)
    <(p → f, h), (p → g, i)> = <(p → f, h), (p → g, i)> 

    <f, (p → g, h)> = p → <f, g> <f, h>
    ≡ Def-Condicional de McCarthy (54)
    <f, (p → g, h)> = [<f, g>, <f, h>]·p?
    ≡ Lei da troca (28)
    <f, (p → g, h)> = <[f, f], [g, h]>·p?
    ≡ Fusão-× (9)
    <f, (p → g, h)> = <[f, f]·p?, [g, h]·p?>
    ≡ Def-Condicional de McCarthy (54)
    <f, (p → g, h)> = <(p → f, f), (p → g, h)>
    ≡ p → k, k = k (Dado no enunciado)
    <f, (p → g, h)> = <f, (p → g, h)>

    p → (p → a, b), (p → c, d) = p → a, d
    ≡ Def-Condicional de McCarthy (54)
    [(p → a, b), (p → c, d)] · p? = p → a, d
    ≡ Def-Condicional de McCarthy (54)
    [[a, b]·p?, [c, d]·p?] · p? = p → a, d
    ≡ Absorção-+ (21)
    ([[a, b], [c, d]] · (p? + p?)) · p? = p → a, d
    ≡ Assoc-comp (2)
    [[a, b], [c, d]] · ((p? + p?) · p?) = p → a, d
    ≡ (p? + p?) · p? = (i1 + i2) · p? (Dado no enunciado)
    [[a, b], [c, d]] · (i1 + i2) · p? = p → a, d
    ≡ Absorção-+ (21)
    [[a, b] · i1, [c, d] · i2] · p? = p → a, d
    ≡ Cancelamento-+ (18)
    [a, [c, d] · i2] · p? = p → a, d
    ≡ Cancelamento-+ (18)
    [a, d] · p? = p → a, d
    ≡ Def-Condicional de McCarthy (54)
    p → a, d = p → a, d
