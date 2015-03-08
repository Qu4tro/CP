
#### 1. Seja dada a funcão `swap = <π2, π1>`. Faca um diagrama que explique o tipo de swap e mostre, usando o cálculo de programas, que `swap · swap = id`, onde id é a funcão identidade.

> TODO - Image

    swap · swap = id
    ≡ Def-swap
    <π2, π1> · swap = id
    ≡ Fusão-×
    <π2 · swap, π1 · swap> = id
    ≡ Def-swap
    <π2 · <π2, π1>, π1 · <π2, π1>> = id
    ≡ Cancelamento-×
    <π1, π1 · <π2, π1>> = id
    ≡ Cancelamento-×
    <π1, π2> = id
    ≡ Reflexão-×
    id = id





