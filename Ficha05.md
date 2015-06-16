Ficha 5
=====================

#### 1. Seja dada uma função ∇ da qual só sabe duas propriedades: `∇ ⋅ i1 = id` e `∇ ⋅ i2 = id`. Mostre que necessariamente, ∇ satisfaz também a propriedade natural `f ⋅ ∇ = ∇ ⋅ (f + f)`.

**R:**
    
    ∇ ⋅ i1 = id
    ∇ ⋅ i2 = id
    ≡ Universal-+ (17)
    ∇ = [id, id]

    f ⋅ ∇ = ∇ ⋅ (f + f)
    ≡ Def-∇
    f ⋅ [id, id] = [id, id] ⋅ (f + f)
    ≡ Absorção-+ (21)
    f ⋅ [id, id] = [id ⋅ f, id ⋅ f]
    ≡ Natural-id (1)
    f ⋅ [id, id] = [f, f]
    ≡ Fusão-+ (20)
    [f ⋅ id, f ⋅ id] = [f, f]
    ≡ Natural-id (1)
    [f, f] = [f, f]

#### 2. Faça a inferência do tipo polimórfico principal (isto é, mais geral) da funcão `<π1 + π1, [π2, π2]>` através de um diagrama e deduza daí a respectiva propriedade natural.

**R:**

    <π1 + π1, [π2, π2]> :: (A × B) + (C × B) -> (A + C) × B

![Diagram of free property of the function](/images/pis_nat.png)

Propriedade natural

    <π1 + π1, [π2, π2]> ⋅ ((f × g) + (h × g)) = ((f + g) × h) ⋅ <π1 + π1, [π2, π2]>
    
#### 3. Calcule analiticamente a propriedade natural da função `twist = swap · (id × swap)` recorrendo explicitamente as propriedades naturais de `id` e de `swap`.

**R:**


WRONG

    (g × f) ⋅ swap = swap ⋅ (f × g)
    f ⋅ id = id ⋅ f 

    twist ⋅ z = z ⋅ twist
    ≡ Def-twist
    (swap ⋅ (id × swap)) ⋅ x = x ⋅ twist
    ≡ Natural-swap
    (swap × id) ⋅ swap ⋅ x = x ⋅ twist
    ≡ Porque swap leva um split como argumento, expandimos o x
    (swap × id) ⋅ swap ⋅ (f × z) = (f × z) ⋅ twist
    ≡ Def-swap 
    (swap × id) ⋅ <π2, π1> ⋅ (f × z) = (f × z) ⋅ twist
    ≡ Fusão-×
    (swap × id) ⋅ <π2 ⋅ (f × z), π1 ⋅ (f × z)>  = (f × z) ⋅ twist
    ≡ Natural-π1; Natural-π2
    (swap × id) ⋅ <z ⋅ π2, f ⋅ π1>  = (f × z) ⋅ twist
    ≡ Absorção-×; Natural-id
    <swap ⋅ z ⋅ π2, f ⋅ π1>  = (f × z) ⋅ twist
    ≡ Porque swap leva um split como argumento, expandimos o z
    <swap ⋅ (g × h) ⋅ π2, f ⋅ π1>  = (f × (g × h)) ⋅ twist
    ≡ Def-×
    (swap ⋅ (g × h)) × f = (f × (g × h)) ⋅ twist

Não podemos fazer nada, por isso já sabemos a primeira parte da propriedade grátis de twist. Vamos agora descobrir a segunda.

    (f × (g × h)) ⋅ twist
    ≡ Def-twist
    (f × (g × h)) ⋅ (swap ⋅ (id × swap))
    ≡ Assoc-comp (2); Natural-swap
    (swap ⋅ ((g × h) × f)) ⋅ (id × swap)

    

#### 4. 

* Use a propriedade universal da esquerda para demonstrar a lei da reflexão `for succ 0 = id` e propriedade: `for succ 1 = succ`.

    for succ 0 = id
    ≡ Def for
    (|[0, succ]|) = id
    ≡ Def Universal-Cata (37)
    [0, succ] . (id + id) = id . in
    ≡ Def in
    [0, succ] . (id + id) = id . [zero, succ]
    ≡ Def Natural-id
    [0, succ] . (id + id) = [zero, succ]
    ≡ Def Absorção-+
    [0 . id, succ . id] = [zero, succ]
    ≡ Def Natural-id
    [0, succ] = [zero, succ]
    ≡ Def zero
    [0, succ] = [0, succ]
