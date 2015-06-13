Ficha 4
=====================

TODO EVERYTHING

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
    * Escreva a equivalência para o caso `f = assocr` (identifique g).

#### 3. Deduza o tipo mais geral da função `f = (id + π) · i2 · π2` e infira a respectiva propriedade *grátis (natural)* através de um diagrama.

#### 4. Considera a função `iso = <! + !, [id, id]>`

    * Identifique o isomorfismo que ela testemunha, desenhando-a sob a forma de um diagrama de tipos.
    * Derive a partir desse diagrama a proprieda (dita *grátis*) de `iso`,

        (id × f) · iso = iso · (f + f)

    * Confirme, por cálculo analítico, essa propriedade.
    * Derive uma definição em Haskell *pointwise* de iso.

#### 5. Identifique, apoiando a sua resolução num diagrama, qual é a definição da função polimórfica α cuja propriedade natural ("grátis") é

    (f + h) · α = α · (f + g × h)

#### 6. Para o caso de um *isomorfismo h*, a lei de Leibniz transforma-se numa equivalência:

    f · h = g · h ≡ f = g

Recorra a esta propriedade para mostrar uqe a igualdade

    h · distr · (g × (id + f)) = k

é equivalente à igualdade

    h · (g × id + g × f)) = k · undistr

*Sugestão:* não ignore a propriedade natural do isomorfismo distr.


#### 7. Considere a seguinte declaração de um tipo de *árvores binárias*, em Haskell:

    data LTree a = Leaf a | Fork (LTree a, LTree a)

Tendo em conta a função `inLTree = [Leaf, Fork]`, desenha o seu diagrama e calcula a sua inversa

    outLTree :: LTree a -> Either a (LTree a, LTree a)
    outLTree (Leaf a) = i1 a
    outLTree (Fork (x, y)) = i2 (x, y)

#### 8. 

    

