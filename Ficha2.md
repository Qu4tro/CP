Ficha 2
=====================

#### 1. Seja dada a funcão `swap = <π2, π1>`. Faca um diagrama que explique o tipo de swap e mostre, usando o cálculo de programas, que `swap · swap = id`, onde id é a funcão identidade.

**R:**
> TODO - Image

    swap · swap = id
    ≡ Def-swap
    <π2, π1> · swap = id
    ≡ Fusão-× (9)
    <π2 · swap, π1 · swap> = id
    ≡ Def-swap
    <π2 · <π2, π1>, π1 · <π2, π1>> = id
    ≡ Cancelamento-× (7)
    <π1, π1 · <π2, π1>> = id
    <π1, π2> = id
    ≡ Reflexão-× (8)
    id = id

#### 2. Repita a questão anterior para a funcão `coswap = [i2, i1]`.

**R:**
> TODO - Image

    coswap · coswap = id
    ≡ Def-coswap
    coswap · [i2, i1] = id
    ≡ Fusão-+ (20)
    [coswap · i2, coswap · i1] = id
    ≡ Def-coswap
    [[i2, i1] · i2, [i2, i1] · i1] = id
    ≡ Cancelamento-+ (18)
    [i1, [i2, i1] · i1] = id
    [i1, i2] = id
    ≡ Reflexão-+ (19)
    id = id

#### 3. O combinador funcional produto `(f × g) = <f · π1, g · π2>` capta a aplicação *paralela* e *independente* de duas funções.

* Mostre que `(f × g)(x, y) = (f x, g y)` 

**R:**

    (f × g)(x, y) = (f x, g y)
    ≡ Def-× (11)
    <f · π1, g · π2>(x, y) = (f x, g y)
    ≡ Def-split (76)
    ((f · π1) (x, y), (g · π2)(x, y)) = (f x, g y)
    ≡ Def-comp (72)
    (f (π1 (x, y)), g (π2 (x, y))) = (f x, g y)
    ≡ Def-proj (79)
    <f x, g y) = (f x, g y)

* Sem recorrer à alínea anterior, demonstre as igualdades

    `id × id = id`  
    `π1 · (f × g) = f · π1`  
    `π2 · (f × g) = g · π2`

**R:**


    id × id = id
    ≡ Def-× (11)
    <id · π1, id · π2> = id
    ≡ Natural-id (1)
    <π1, π2> = id
    ≡ Reflexão-× (8)
    id = id
    

    π1 · (f × g) = f · π1
    ≡ Def-× (11)
    π1 · <f · π1, g · π2> = f · π1
    ≡ Cancelamento-× (7)
    f · π1 = f · π1


    π2 · (f × g) = g · π2
    ≡ Def-× (11)
    π2 · <f · π1, g · π2> = g · π2
    ≡ Cancelamento-× (7)
    g · π2 = g · π2

#### 4. O combinador funcional *soma* define-se por: `f + g = [i1 · f, i2 · g]`

Identifique os nomes das seguintes propriedades

`id + id = id`  
`(f + g) · i1 = i1 · f`  
`(f + g) · i2 = i2 · g`  

no **formulário** da disciplina e demonstre-as usando o cálculo de programas.

**R:**

    id + id = id 
    ≡ Def-+ (22)
    [i1 · id, i2 · id] = id
    ≡ Natural-id (1)
    [i1, i2] = id
    ≡ Reflexão-+ (8)
    id = id

    (f + g) · i1 = i1 · f
    ≡ Def-+ (21)
    [i1 · f, i2 · g] · i1 = i1 · f
    ≡ Cancelamento-+ (18)
    i1 · f = i1 · f 
    
    (f + g) · i2 = i2 · g
    ≡ Def-+ (21)
    [i1 · f, i2 · g] · i2 = i2 · g
    ≡ Cancelamento-+ (18)
    i2 · g = i2 · g 
 
#### 5. Considere as funções seguintes:

    f = <π1 · π1 , π2 × id>
    g = <id × π1 , π2 · π2>

* Identifique, justificadamente, os seus tipos
    
    **R:**

        f :: ((A × B) × C) -> (A × C)

        f1 :: ((A × B) × C) -> A
        f1 = π1 · π1

        f2 :: (A × C) -> C
        f2 = π2 × id

    > Pelo split sabemos que o input de `f` vai ser igual ao de `f1` e de `f2`. O output será um par de output de `f1`(A) e do output de `f2`(C) que resulta em `(A × C)`.

        g :: (A × (B × C)) -> (A × C)

        g :: (A × B)) -> A
        g1 = id × π1

        g :: (A × (B × C)) -> C
        g2 = π2 · π2

    > Pelo split sabemos que o input de `g` vai ser igual ao de `g1` e de `g2`. O output será um par de output de `g1`(A) e do output de `g2`(C) que resulta em `(A × C)`.

* Mostre que `f · g = id`

    **R:**

        f = <π1 · π1 , π2 × id>
        g = <id × π1 , π2 · π2>

        f · g = id
        ≡ Def-f
        <n1 · π1 , π2 × id> · g = id
        ≡ Fusão-× (9)
        <n1 · π1 · g, (π2 × id) · g> = id
        ≡ Def-g
        <n1 · π1 · <id × π1 , π2 · π2>, (π2 × id) · g> = id
        ≡ Cancelamento-× (7)
        <n1 · (id × π1), (π2 × id) · g> = id
        ≡ Def-× (11)
        <n1 · <id · π1, π1 · π2>, (π2 × id) · g> = id
        ≡ Cancelamento-× (7)
        <id · π1, (n2 × id) · g> = id
        ≡ Natural-id (1)
        <π1, (n2 × id) · g> = id
        ≡ Def-g
        <π1, (n2 × id) · <id × π1 , π2 · π2>> = id
        ≡ Absorção-× (10)
        <π1, <n2 · (id × π1), id · π2 · π2>> = id
        ≡ Natural-id (1)
        <π1, <n2 · (id × π1), π2 · π2>> = id
        ≡ Natural-n2 (13)
        <π1, <n1 · π2, π2 · π2>> = id
        ≡ Fusão-× (9)
        <π1, <n1, π2> · π2> = id
        ≡ Reflexão-× (8)
        <π1, id · π2> = id
        ≡ Natural-id (1)
        <π1, π2> = id
        ≡ Reflexão-× (8)
        id = id


#### 6. Todas as leis do cálculo dos combinadores `<f, g>` e `[f, g]` podem ser derivadas das respectivas *propriedades universais*, respectivamente.

* Indentifique-as no formulário disponível na página *web* da disciplina.

**R:**

> Universal-× (6) e Universal-+ (17).

* Use a segunda para demonstrar a lei `[i1, i2] = id` conhecido por *Reflexão-+*.

**R:**

    [i1, i2] = id
    ≡ Universal-+
    [i1, i2] ≡ [i1, i2].i1 = i1
               [i1, i2].i2 = i2
    ≡ Natural-id
    id = id

* Use a primeira para demonstrar a lei

        [f, g] = [h, k] ≡ f = h
                          g = k
        
    que também consta desse formulário sob a designação *Eq-+*.

**R:**

    TODO


#### 7. Considera uma função *d* da qual apenas conhece duas propriedades:

    π1 · d = id
    π2 · d = id

Mostre, recorrendo directamente à propriedade universal correspondente que essa função é, necessariamente, a mesma que em Programação Funcional escreveria da forma seguinte, em Haskell:

    d :: a -> (a, a)
    d a = (a, a)

**R:**

    π1 · d = id
    π2 · d = id
    ≡Universal-× (6)
    d = <id, id>
    ≡Igualdade extensional (71)
    d a = <id, id> a
    ≡Def-split (76)
    d a = (id a, id a)
    ≡Def-id (73)
    d a = (a, a)

#### 8. Identifique os tipos das expressoes. Como compara este último com o tipo da funcão *d* da alínea anterior?

**R:**

    <π1, <id, π2>> :: (A × B) -> (A × ((A × B) × B))
    <id, <π1, π2>> :: (A × B) -> ((A × B) × (A × B))

> O tipo da segunda função é um caso especifico da função *d*, em que o elemento recebido é um par.




