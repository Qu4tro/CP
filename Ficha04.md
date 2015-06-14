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

    f = (id + π1) ⋅ i2 ⋅ π2
    ≡ Natural-i2 (24)
    f = i2 . π1 ⋅ π2


    f :: A × (B × C) -> _ + C

![Diagram of free property of f](/images/f_nat.png)

Propriedade grátis: 

     f ⋅ (j × (g × h)) = (i + h) ⋅ f


#### 4. Considera a função `iso = <! + !, [id, id]>`

* Identifique o isomorfismo que ela testemunha, desenhando-a sob a forma de um diagrama de tipos.

    A + A ≅ (1 + 1) × A  
    ≡  
    A + A ≅ 2 × A

![Diagram of iso's isomorphism](/images/iso_iso.png)


* Derive a partir desse diagrama a proprieda (dita *grátis*) de `iso`,

    (id × f) · iso = iso · (f + f)

* Confirme, por cálculo analítico, essa propriedade.

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

![Diagram of alpha's natural property](/images/alpha_nat.png)

    α :: A + (B × C) -> A + C
    α = id + p2

Se o argumento estiver encapsulado por i1 devolve-lo como o recebemos.
Se o argumento estiver encapsulado por i2 devolver o 2º elemento do split.

#### 6. Para o caso de um *isomorfismo h*, a lei de Leibniz transforma-se numa equivalência:

    f · h = g · h ≡ f = g

Recorra a esta propriedade para mostrar uqe a igualdade

    h · distr · (g × (id + f)) = k

é equivalente à igualdade

    h · (g × id + g × f)) = k · undistr

*Sugestão:* não ignore a propriedade natural do isomorfismo distr.


#### 7. Considere a seguinte declaração de um tipo de *árvores binárias*, em Haskell:

    data LTree a = Leaf a | Fork (LTree a, LTree a)

Tendo em conta a função `inLTree = [Leaf, Fork]`, calcula a sua inversa

    outLTree :: LTree a -> Either a (LTree a, LTree a)
    outLTree (Leaf a) = i1 a
    outLTree (Fork (x, y)) = i2 (x, y)

resolvendo a equação `outLTree . inLTree = id` em ordem a `outLTree`.

#### 8. 

    

