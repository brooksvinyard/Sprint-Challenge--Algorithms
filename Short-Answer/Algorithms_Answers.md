Add your answers to the Algorithms exercises here.

## Exercise I

```
a)  a = 0                       O(c)
    while (a < n * n * n):      O(3n)
      a = a + n * n             O(2n)
```
It all simplifies down to O(n)


```
b)  sum = 0                                 O(c)
    for i in range(n):                      O(n)
      i += 1                                O(c)
      for j in range(i + 1, n):             O(n)
        j += 1                              O(c)
        for k in range(j + 1, n):           O(n)
          k += 1                            O(c)
          for l in range(k + 1, 10 + k):    O(n)
            l += 1                          O(c)
            sum += 1                        O(c)
```
It all simplifies down to O(n)


```
c)  def bunnyEars(bunnies):             
      if bunnies == 0:                  O(c)
        return 0                        O(c)

      return 2 + bunnyEars(bunnies-1)   O(n) # Each call makes 1 more call
```
It all simplifies down to O(n)


## Exercise II

Suppose that you have an _n_-story building and plenty of eggs. Suppose also that an egg gets broken if it is thrown off floor _f_ or higher, and doesn't get broken if dropped off a floor less than floor _f_. Devise a strategy to determine the value of _f_ such that the number of dropped eggs is minimized.

Write out your proposed algorithm in plain English or pseudocode and give the runtime complexity of your solution.


In order to determine what highest the floor of the building is that I can drop an egg without breaking it:

I would determine **n//2 = pivot** and drop an egg from that floor
    This would allow me to rule out half of the floors

    if egg breaks = True:
        => I know that all the floors above the pivot WOULD also break the egg
        => I would make a new pivot halfway between the pivot and 0 (the ground) 
        => Drop another egg
    
    if egg breaks = False:
        => I know that all the floors below the pivot WOULD NOT break the egg
        => I would make a new pivot halfway between the pivot and n (the top floor) 
        => Drop another egg

By using the pivot, and ruling out half the floors at a time I will eventually determine the hightest floor I can drop the egg from without it breaking.

Because the number of posible floors gets cut in half each time:
    Runtime complexity = O(log n)