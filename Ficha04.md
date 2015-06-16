Ficha 4
=====================

#### 1. Considere a função `coassocr = [id + i1, i2 · i2]`. Calcule a sua conversa `coassocl` a partir da equação `coassocl . coassocr = id`

*Sugestão:* Faça-o resolvendo em ordem a x, y e z a seguinte versão dessa equação:

    [x, [y, z]] . [id + i1, i2 . i2] = id

**R:**

    [x, [y, z]] . [id + i1, i2 . i2] = id
    ≡ 
    [x, [y, z]] . [[i1 . id, i2 . i1], i2 . i2] = id
    ≡ 
    [x, [y, z]] . [[i1, i2 . i1], i2 . i2] = id
    ≡ 

#### 2. Sejam dadas, em geral, duas funções `f` e `g` satisfazendo a propriedade

    f y = x    ≡    y = g x

* Mostre que `f` e `g` são inversas uma das outra.

**R:**

    f y = x
    ≡ Def-y
    f (g x) = x
    ≡ Def-comp (72)
    (f ⋅ g) x = x
    ≡ Natural-id (1)
    (f ⋅ g) x = id x 
    ≡ Igualdade extensional (71)
    (f ⋅ g) = id

* Escreva a equivalência para o caso `f = assocr` (identifique g).

**R:**

    assocr :: (A × B) × C -> A × (B × C)
    assocr = <π1 ⋅ π1, <π2 ⋅ π1, π2>>

    assocl :: A × (B × C) -> (A × B) × C

    (f ⋅ g) = id
    ≡ Def-f
    (assocr ⋅ g) = id
    ≡ Def-assocr
    (<π1 ⋅ π1, <π2 ⋅ π1, π2>> ⋅ g) = id
    ≡ Fusão-× (9)
    <π1 ⋅ π1 ⋅ g, <π2 ⋅ π1, π2> ⋅ g> = id
    ≡ Fusão-× (9)
    <π1 ⋅ π1 ⋅ g, <π2 ⋅ π1 ⋅ g, π2 ⋅ g>> = id
    ≡ Def-id (Para o tipo de assocl)
    <π1 ⋅ π1 ⋅ g, <π2 ⋅ π1 ⋅ g, π2 ⋅ g>> = <π1, <π1, π2> ⋅ π2>
    ≡ Eq-× (16)
    π1 ⋅ π1 ⋅ g = π1
    <π2 ⋅ π1 ⋅ g, π2 ⋅ g>> = <π1, π2> ⋅ π2>
    ≡ Eq-× (16)
    π1 ⋅ π1 ⋅ g = π1
    π2 ⋅ π1 ⋅ g = <π1, π2>
    π2 ⋅ g      = π2
    ≡ Universal-× (17)
    π1 ⋅ g = <π1, <π1, π2>>
    π2 ⋅ g = π2
    ≡ Universal-× (17)
    g = <<π1, <π1, π2>>, π2>
    

    answer: <<π1, π1 . π2>, π2 . π2>

TODO

#### 3. Deduza o tipo mais geral da função `f = (id + π1) · i2 · π2` e infira a respectiva propriedade *grátis (natural)* através de um diagrama.

**R:**

    f = (id + π1) ⋅ i2 ⋅ π2
    ≡ Natural-i2 (24)
    f = i2 . π1 ⋅ π2

    f :: A × (B × C) -> _ + C

![Diagram of free property of f](/images/f_nat.png)

Propriedade grátis: 

     f ⋅ (j × (g × h)) = (i + h) ⋅ f


#### 4. Considera a função `iso = <! + !, [id, id]>`

* Identifique o isomorfismo que ela testemunha, desenhando-a sob a forma de um diagrama de tipos.

**R:**

    A + A ≅ (1 + 1) × A  
    ≡  
    A + A ≅ 2 × A

![Diagram of iso's isomorphism](/images/iso_iso.png)


* Derive a partir desse diagrama a proprieda (dita *grátis*) de `iso`,

    (id × f) · iso = iso · (f + f)

* Confirme, por cálculo analítico, essa propriedade.

**R:**

        (id × f) · iso = iso · (f + f)
        ≡ Def-iso
        (id × f) · <! + !, [id, id]> = iso · (f + f)
        ≡ Absorção-× (10)
        <id ⋅ (! + !), f ⋅ [id, id]> = iso · (f + f)
        ≡ Natural-id (1)
        <! + !, f ⋅ [id, id]> = iso · (f + f)
        ≡ Fusão-+ (20)
        <! + !, [f ⋅ id, f ⋅ id]> = iso · (f + f)
        ≡ Natural-id (1)
        <! + !, [f, f]> = iso · (f + f)
        ≡ Def-+ (22)
        <[i1 ⋅ !, i2 ⋅ !], [f, f]> = iso · (f + f)
        ≡ Lei da troca (28)
        [<i1 ⋅ !, f>, <i2 ⋅ !, f>] = iso · (f + f)
        ≡ Natural-id (1)
        [<i1 ⋅ !, id ⋅ f>, <i2 ⋅ !, id ⋅ f>] = iso · (f + f)
        ≡ Natural-const (3)
        [<i1 ⋅ ! ⋅ f, id ⋅ f>, <i2 ⋅ ! ⋅ f, id ⋅ f>] = iso · (f + f)
        ≡ Fusão-× (9)
        [<i1 ⋅ !, id> ⋅ f, <i2 ⋅ !, id> ⋅ f] = iso · (f + f)
        ≡ Absorção-+ (10)
        [<i1 ⋅ !, id>, <i2 ⋅ !, id>] · (f + f) = iso · (f + f)
        ≡ Lei da troca (28)
        <[i1 ⋅ !, i2 ⋅ !], [id, id]> · (f + f) = iso · (f + f)
        ≡ Def-+ (22)
        <! + !, [id, id]> · (f + f) = iso · (f + f)
        ≡ Def-iso 
        iso · (f + f) = iso · (f + f)


* Derive uma definição em Haskell *pointwise* de iso.

**R:**

        iso = <! + !, [id, id]>
        ≡ Def-+ (22)
        iso = <[i1 ⋅ !, i2 ⋅ !], [id, id]>
        ≡ Lei da troca (28)
        iso = [<i1 ⋅ !, id>, <i2 ⋅ !, id>]
        ≡ Universal-+ (17)
        iso . i1 = <i1 ⋅ !, id>
        iso . i2 = <i2 ⋅ !, id>
        ≡ Igualdade extensional (71)
        (iso . i1) x = <i1 ⋅ !, id> x
        (iso . i2) x = <i2 ⋅ !, id> x
        ≡ Def-comp (72)
        iso (i1 x) = <i1 ⋅ !, id> x
        iso (i2 x) = <i2 ⋅ !, id> x
        ≡ Def-split (76)
        iso (i1 x) = ((i1 ⋅ !) x, id x)
        iso (i2 x) = ((i2 ⋅ !) x, id x)
        ≡ Def-id (73)
        iso (i1 x) = ((i1 ⋅ !) x, x)
        iso (i2 x) = ((i2 ⋅ !) x, x)
        ≡ Assoc-comp (2)
        iso (i1 x) = (i1 ⋅ (! x), x)
        iso (i2 x) = (i2 ⋅ (! x), x)
        ≡ Def-comp (72)
        iso (i1 x) = (i1 (! x), x)
        iso (i2 x) = (i2 (! x), x)
        ≡ Def-!
        iso (i1 x) = (i1 (), x)
        iso (i2 x) = (i2 (), x)


#### 5. Identifique, apoiando a sua resolução num diagrama, qual é a definição da função polimórfica α cuja propriedade natural ("grátis") é

    (f + h) · α = α · (f + g × h)

**R:**

![Diagram of alpha's natural property](/images/alpha_nat.png)

    α :: A + (B × C) -> A + C
    α = id + p2

Se o argumento estiver encapsulado por i1 devolve-lo como o recebemos.
Se o argumento estiver encapsulado por i2 devolver o 2º elemento do split.

#### 6. Para o caso de um *isomorfismo h*, a lei de Leibniz transforma-se numa equivalência:

    f · h = g · h ≡ f = g

Recorra a esta propriedade para mostrar que a igualdade

    h · distr · (g × (id + f)) = k

é equivalente à igualdade

    h · (g × id + g × f)) = k · undistr

*Sugestão:* não ignore a propriedade natural do isomorfismo distr.

TODO

#### 7. Considere a seguinte declaração de um tipo de *árvores binárias*, em Haskell:

    data LTree a = Leaf a | Fork (LTree a, LTree a)

Tendo em conta a função `inLTree = [Leaf, Fork]`, calcula a sua inversa

    outLTree :: LTree a -> Either a (LTree a, LTree a)
    outLTree (Leaf a) = i1 a
    outLTree (Fork (x, y)) = i2 (x, y)

resolvendo a equação `outLTree ⋅ inLTree = id` em ordem a `outLTree`⋅

**R:**

    outLTree ⋅ inLTree = id
    ≡ Def-inTree
    outLTree ⋅ [Leaf, Fork] = id
    ≡ Fusão-+ (20)
    [outLTree ⋅ Leaf, outLTree ⋅ Fork] = id
    ≡ Reflexão-+ (19)
    [outLTree ⋅ Leaf, outLTree ⋅ Fork] = [i1, i2]
    ≡ Eq-+ (27)
    outLTree ⋅ Leaf = i1
    outLTree ⋅ Fork = i2
    ≡ Igualdade extensional (71)
    (outLTree ⋅ Leaf) x = i1 x
    (outLTree ⋅ Fork) (x, y) = i2 (x, y)
    ≡ Def-comp (72)
    outLTree (Leaf x) = i1 x
    outLTree (Fork (x, y)) = i2 (x, y)
    

#### 8. Recorde a função `map :: (a -> b) -> [a] -> [b]`. Assumindo como válida a seguinte propriedade dessa função,

    k = map f ≡ k ⋅ [nil, cons] = [nil ⋅ cons] ⋅ (id + f × k)

para `k` do mesmo tipo que `map f` e em que `cons (a, x) = a:x` e `nil x = []`, demonstre os factos seguintes:

           map id = id
    (map f) . nil = nil
      map f (a:x) = (f a) : (map f x)

**R:**

    k ⋅ [nil, cons] = [nil, cons] ⋅ (id + (f × k))
    ≡ Def-k
    (map id) ⋅ [nil, cons] = [nil, cons] ⋅ (id + (f × (map id)))
    ≡ Def-f
    (map id) ⋅ [nil, cons] = [nil, cons] ⋅ (id + (id × (map id)))
    ≡ Def-(map id)
    (map id) ⋅ [nil, cons] = [nil, cons] ⋅ (id + (id × id))
    ≡ Functor-id-× (15)
    (map id) ⋅ [nil, cons] = [nil, cons] ⋅ (id + id)
    ≡ Functor-id-+ (26)
    (map id) ⋅ [nil, cons] = [nil, cons] ⋅ id
    ≡ Natural-id (1)
    (map id) ⋅ [nil, cons] = [nil, cons]
    ≡ Natural-id (1)
    (map id) ⋅ [nil, cons] = id ⋅ [nil, cons]
    ≡ Leibniz (5)
    map id = id

**R:**

    (map f) ⋅ [nil, cons] = [nil, cons] ⋅ (id + (f × k))
    ≡ Fusão-× (9)
    [map f ⋅ nil, map f ⋅ cons] = [nil, cons] ⋅ (id + (f × k))
    ≡ Absorção-+ (21)
    [map f ⋅ nil, map f ⋅ cons] = [nil ⋅ id, cons ⋅ (f × k)]
    ≡ Eq-+ (27)
    (map f) ⋅ nil = nil ⋅ id
    (map f) ⋅ cons = cons ⋅ (f × k)
    ≡ Natural-id (1)
    (map f) ⋅ nil = nil
    (map f) ⋅ cons = cons ⋅ (f × k)

    
**R:**

    (map f) ⋅ [nil, cons] = [nil, cons] ⋅ (id + (f × (map f)))
    ≡ Fusão-× (9)
    [map f ⋅ nil, map f ⋅ cons] = [nil, cons] ⋅ (id + (f × (map f)))
    ≡ Absorção-+ (21)
    [map f ⋅ nil, map f ⋅ cons] = [nil ⋅ id, cons ⋅ (f × (map f))]
    ≡ Eq-+ (27)
    (map f) ⋅ nil = nil ⋅ id
    (map f) ⋅ cons = cons ⋅ (f × (map f))
    ≡ Natural-id (1)
    (map f) ⋅ nil = nil
    (map f) ⋅ cons = cons ⋅ (f × (map f))
    ≡ Def-f
    (map f) ⋅ nil = nil
    (map f) ⋅ cons = cons ⋅ (f × (map f))
    ≡ Igualdade extensional (71)
    ((map f) ⋅ nil) x = nil x
    ((map f) ⋅ cons) (a, x) = (cons ⋅ (f × (map f))) (a, x)
    ≡ Def-comp (72)
    map f (nil x) = nil x
    map f (cons (a, x)) = cons ((f × (map f)) (a, x))
    ≡ Def-nil
    map f [] = []
    map f (cons (a, x)) = cons ((f × (map f)) (a, x))
    ≡ Def-x (77)
    map f [] = []
    map f (cons (a, x)) = cons (f a, map f x)
    ≡ Def-cons
    map f [] = []
    map f (a:x) = (f a):(map f x)

    
#### 9⋅ Mostre que a função `for b i`, é solução da equação seguinte, em x: `x ⋅ in = [i, b] ⋅ (id + x)`, onde:

    for b i 0 = i
    for b i (n + 1) = b (for b i n)

    in = [0, succ]
    succ n = n + 1


**R:**

    x ⋅ in = [i, b] ⋅ (id + x)
    ≡ Def-in
    x ⋅ [0, succ] = [i, b] ⋅ (id + x)
    ≡ Fusão-+ (20)
    [x ⋅ 0, x ⋅ succ] = [i, b] ⋅ (id + x)
    ≡ Absorção-+ (21)
    [x ⋅ 0, x ⋅ succ] = [i ⋅ id, b ⋅ x]
    ≡ Natural-id (1)
    [x ⋅ 0, x ⋅ succ] = [i, b ⋅ x]
    ≡ Eq-+ (27)
    x ⋅ 0 = i
    x ⋅ succ = b ⋅ x
    ≡ Igualdade extensional (71)
    (x ⋅ 0) n = i n
    (x ⋅ succ) n = (b ⋅ x) n
    ≡ Def-comp (72)
    x (0 n) = i n
    x (succ n) = b (x n)
    ≡ Fusão-const (4)
    x 0 = i
    x (succ n) = b (x n)
    ≡ Def-succ
    x 0 = i
    x (n + 1) = b (x n)
    ≡ Def-x
    for b i 0 = i
    for b i (n + 1) = b (for b i n)
