Goal: determine how runtime/number of operations scales up as the input scales up. How much longer does it take to run as the size of the data to process gets bigger?

## Steps to compute Big O

* Things in sequence that _aren't_ loops add together
* A single thing inside a loop gets multiplied by the loop

1. Go a line at a time, only looking at lines that are executable
2. Add all the things in sequence that you can first
3. Then multiply by the loops
4. Then repeat steps 2-3 as many times as you can
5. Then keep the dominant term from the resulting sum(s)
6. Then drop constants

## Hints

* Individual statements tend to be `O(1)`.
* Loop statements tend to be `O(how-many-times-they-loop)`.
* Anything that doubles the runtime each step is `O(2^n)` (e.g. naive Fibonacci).
* Anything that triples the runtime each step is `O(3^n)`.
* Anything that halves the runtime each step is `O(log n)` (e.g. binary search).
* By _dominant term_ we mean, "thing which is largest given some large value of _n_, like 10000".

## Gotchas

* Built in functions might incur significant Big O without you noticing. Python's list `.copy()` might seem like just a simple `O(1)` line, but [it's `O(n)` under the hood](https://wiki.python.org/moin/TimeComplexity).
* Beware of loops that modify their index in weird ways.

## Example

Label all statements by their time complexities. Individual statements get their Big O, while loops get the number of times they loop.

```python
def foo(n):
    a = 10                # O(1)
    b = 20                # O(1)

    for i in range(n):    # O(n)
        a += b               # O(1)
        b += 1               # O(1)

    for j in range(n**2): # O(n^2)
        a -= 2               # O(1)
        print(a)             # O(1)

        for k in range(n/2): # O(n/2)
            print(k)             # O(1)

    return a + b          # O(1)
```

Now we'll replace the lines of code with their Big O for brevity:

```python
def foo(n):
    # O(1)
    # O(1)

    # O(n)
        # O(1)
        # O(1)

    # O(n^2)
        # O(1)
        # O(1)

        # O(n/2)
            # O(1)

    # O(1)
```

Try to add things in sequence, but remember that loops interrupt sequences!


```python
def foo(n):
    # O(2)    -- was O(1) + O(1)

    # O(n)
        # O(2)    -- was O(1) + O(1)

    # O(n^2)
        # O(2)    -- was O(1) + O(1)

        # O(n/2)
            # O(1)

    # O(1)
```

Now we see if we can multiply any loops by their bodies.

```python
def foo(n):
    # O(2)

    # O(2 * n)    -- had body O(2)

    # O(n^2)      -- can't do this one yet--body has more than one item
        # O(2)

        # O(1 * n/2)    -- had body O(1)

    # O(1)
```

Let's try to add any sequences again.


```python
def foo(n):
    # O(2 + 2 * n)

    # O(n^2)
        # O(2 + 1 * n/2)

    # O(1)
```

Now let's try multiplying loops again

```python
def foo(n):
    # O(2 + 2 * n)

    # O(n^2 * (2 + 1 * n/2))

    # O(1)
```

Add add sequences again:

```python
def foo(n):
    # O((2 + 2 * n) + (n^2 * (2 + 1 * n/2)) + 1)
```

Now we're down to one line. That's the time complexity, but we need to reduce it.

Break out your algebra.

```
(2 + 2 * n) + (n^2 * (2 + 1 * n/2)) + 1   From the Big O, above
2 + 2 * n + n^2 * (2 + 1 * n/2) + 1       Lose unnecessary parens
3 + 2 * n + n^2 * (2 + 1 * n/2)           Add some like terms
3 + 2 * n + n^2 * (2 + n/2)               1* is does nothing
3 + 2 * n + 2 * n^2 + n/2 * n^2           Distribute n^2
3 + 2 * n + 2 * n^2 + 1/2 * n * n^2       Note the n/2 is 1/2*n
3 + 2 * n + 2 * n^2 + 1/2 * n^3           n * n^2 = n^3
(3) + (2 * n) + (2 * n^2) + (1/2 * n^3)   Choose the most dominant from the sum
1/2 * n^3                                 1/2 * n^3 grows fastest, is dominant
n^3                                       Drop the constant
```

`O(n^3)` is the time complexity of this function.

With practice, you can do this in your head. Looking back, the nested loop _must_ have been where the function spent the most of its time; an experienced dev would see that and just quickly compute the Big O for that function.

