
Найти `n`-ое число в последовательности Фибоначи.

Входные данные: 
    `n` -- целое неотрицательное число
Выходные данные:
    `f` -- целое неотрицательное число

S:
```
    input(n)
    if n == 0:
        output(0)
        exit() # прекращает выполнение

    i = 1
    prev, curr = 0, 1

    while i != n:
        temp = curr
        curr = curr + prev
        prev = temp
        i = i + 1

    output(curr)
    exit()
``` 

Предусловие: P: 
    n -- целое неотрицательное
Постусловие Q:
    Fib = { F_0 = 0; F_1 = 1; F_k+2 = F_k+1 + F_k }
    (curr = A_n) ∧ (A_n ∈ Fib)
Доказать {P} S {Q}

Доказательство:

0. P -> (n ∈ Z) ∧ ((n = 0) V (n = 1) V (n > 1))
1. ](n = 0) => (f = A0); `output(0)`; 0 ∈ Fib; верно
2. `i = 1`; `prev, curr = 0, 1` =>
   prev, curr = F_0, F_1 ~ prev, curr = F_i-1, F_i;
   `while i != n`
3. ](n = 1); 
   (n = 1) -> (f = F_1 = 1); (n = i) => `output(curr)`;
   curr = 1 = F_1, верно
4. ](n > 1)
   (n > 1) -> (f = F_n); 
   ```
        temp = curr
        curr = curr + prev
        prev = temp
        i = i + 1
   ```
   curr = curr + prev = F_i + F_i-1 = F_i+1;
   prev = F_i
5. (n = i) ? `goto 4.`, (n = i) => curr = F_i = F_n, верно