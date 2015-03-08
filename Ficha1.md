Ficha 1
=====================

#### 1. Codifique em Haskell as funcões `length :: [a] -> Int` e  `reverse :: [a] -> [a]`que conhece da disciplina de Programação Funcional (PF) e que, respectivamente, calculam o comprimento da lista de entrada e a invertem.

**R:**

    length1 :: [a] -> Int
    length1 [] = 0
    length1 (_:xs) = 1 + length xs

    reverse1 :: [a] -> [a]
    reverse1 [] = []
    reverse1 (x:xs) = reverse xs ++ [x]

#### 2. Recorde o tipo que se usa em Haskell para representar valores opcionais:

    data Maybe a = Nothing | Just a
   
Defina a funcão `catMaybes :: [Maybe a] -> [a]`que extrai o conteúdo útil da lista de entrada.

**R:**

    catMaybes :: [Maybe a] -> [a]
    catMaybes [] = []
    catMaybes (Nothing: xs)  =     catMaybes xs
    catMaybes ((Just x):xs) = x : catMaybes xs

#### 3. Apresente definições em Haskell das seguintes funções que estudou em PF:

`uncurry :: (a -> b -> c) -> (a, b) -> c`(que emparelha os argumentos de uma função)  
`curry :: ((a, b) -> c) -> a -> b -> c`(que faz o efeito inverso da anterior)  
`flip :: (a -> b -> c) -> b -> a -> c`(que troca a ordem dos argumentos de uma função)

**R:**

    uncurry :: (a -> b -> c) -> (a, b) -> c
    uncurry f (a, b) = f a b

    curry :: ((a, b) -> c) -> a -> b -> c
    curry f a b = f (a, b)

    flip :: (a -> b -> c) -> b -> a -> c
    flip f b a = f a b

#### 4. Considere a seguinte declaração de um tipo de *árvores binárias*, em Haskell:

    data LTree a = Leaf a | Fork (LTree a, LTree a)

Codifique as funções seguintes:

* `flatten :: LTree a -> [a]`- que deverá dar a lista de elementos da árvore argumento
* `mirror :: LTree a -> LTree a`- que deverá espelhar a árvore argumento
* `fmap :: (b -> a) -> LTree b -> LTree a`- que deverá transformar cada folha *x* da árvore argumento na folha *f x*

**R:**

        flatten :: LTree a -> [a]
        flatten (Leaf a) = [a]
        flatten (Fork (leftBranch, rightBranch)) = flatten leftBranch ++ flatten rightBranch

        mirror :: LTree a -> LTree a
        mirror (Leaf a) = Leaf a
        mirror (Fork (leftBranch, rightBranch)) = Fork (mirror rightBranch, mirror leftBranch)

        fmap1 :: (b -> a) -> LTree b -> LTree a
        fmap1 f (Leaf a) = Leaf (f a)
        fmap1 f (Fork (leftBranch, rightBranch)) = Fork (fmap1 f leftBranch, fmap1 f rightBranch)

#### 5. A composição de funções define-se, emm Haskell, tal como na matemática:

     `f · g) x = f (g x`)

* Calcula `f · g) x`para os casos seguintes:

    **R:**

        f1 x = 2 * x
        g1 x = x + 1
        f1g1 x = 2 * (x + 1)

        f2 x = succ
        g2 x = 2 * x
        f2g2 x = succ (2 * x)

        f3 x = succ
        g3 x = length
        f3g3 x = succ (length x)

        f4 = succ . (2*)
        g4 (x, y) = x + y
        f4g4 (x, y) = succ (2 * (x + y))

* Mostre que `f · g) · h = f · (g · h)`quaisquer que sejam f, g e h.

    **R:**

        ≡ Igualdade extensional (71)
            ((f · g) · h) x = (f · (g · h)) x
        ≡ Def-comp (72)
            (f · g) (h x) = f ((g · h)) x)
            f (g (h x))   = f (g (h x))

* A função `id :: a -> a`é tal que `id x = x`. Mostre que `f · id = id · f = f`qualquer que seja `f`.

    **R:** 

        f · id = f
        ≡ Igualdade extensional (71)
            (f · id) x = f x
        ≡ Def-comp (72)
            f (id x) = f x
        ≡ Def-id (73)
            f x = f x


        id · f = f
        ≡ Igualdade extensional (71)
            (id · f) x = f x
        ≡ Def-comp (72)
            id (f x) = f x
        ≡ Def-id (73)
            f x = f x


#### 6. Atente na definição seguinte de um dos combinadores emblemáticos da linguagem Haskell, que já conhece de PF:
        
    foldr :: (a -> b -> b) -> b -> [a] -> b
    foldr g z []     = z
    foldr g z (x:xs) = x `g` (foldr g z xs)

* Defina `length :: [a] -> Int`using foldr.

    **R:** 

        length2 :: [a] -> Int
        length2 xs = foldr (\_ n -> succ n) 0 xs
        

* O que faz a função `f = foldr (:) []`? **Sugestão**: comece por copiar a definição dada e faça literalmente as substituições `g := (:)`e `z := []`. De seguida substitua `foldr (:) []`por `f`. Obtém assim uma definição explícita de f, sem recorrer ao combinador dado, que e mais fácil de inspeccionar.

    **R:** 

        f []     = []
        f (x:xs) = x : (f xs)

    A função `f`é a função identidade para uma lista.


#### 7. Re-defina a função

    concat1 :: [[a]] -> [a]
    concat1 = foldr (++) []

sem recorrer ao combinador foldr (Sugestão: faça como na questão 6).

**R:**

    concat2 :: [[a]] -> [a]
    concat2 [] = []
    concat2 (x:xs) = x ++ (concat xs)

#### 8. Diga por palavras suas o que faz a função

    f :: [Int] -> [Int]
    f s = [a + 1 | a <- s, a > 0]

e escreva-a sob a forma de um foldr.

**R:** Esta função remove todos os números não-positivos e incrementa por um todos os restantes.

        ffold :: [Int] -> [Int]
        ffold s = foldr (\x xs -> if x > 0 then ((x + 1):xs) else xs) [] s

#### 9. Considera a função *m* seguinte:

    m :: (a -> b) -> [a] -> [b]
    m f [] = []
    m f (h:t) = (f h) : m f t

* Reescreva-a *usando* o combinador foldr.

    **R:**

        m1 :: (a -> b) -> [a] -> [b]
        m1 f [] = []
        m1 f xs = foldr (\y ys -> (f y):ys) [] xs

* Reescreva-a *sem usar* o combinador foldr.

    **R:** 

        m2 = map

* Qual o tipo de expressão `m (\x -> [x])`? E o que faz essa expressão?

        m (\x -> [x]) :: [a] -> [[a]]

    **R:** Esta expressão transforma cada elemento da lista dada, numa lista que contêm apenas o elemento original.

    Exemplo: 

               > m (\x -> [x]) [4, 1, 3, 7]
               [[4], [1], [3], [7]]
            

* Abreviando a função `x -> [x]`pela designação *singl*, averigue qual o resultado das expressões
            
        let s = m singl "Calculo de Programas"
        in concat s

    e
            
        concat (singl "Calculo de Programas")

    correndo-as mentalmente. Tente generalizar o que apurou nesse exercício mental.
        
    **R:** Em ambas as expressões, o resultado é a string dada como argumento. Na primeira expressão, a funçao (m singl) vai separar a string, numa lista de strings, em que cada uma contém um dos carácteres, em seguinda junta-as todas de novo usando o concat.  
    No segundo caso, ao usar o singl, vai returnar uma lista com um só elemento: a string dada. Ao usar concat nesta lista gerada, vamos receber a string original.
        
