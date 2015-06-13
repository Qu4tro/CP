Ficha 4
=====================

TODO EVERYTHING

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
