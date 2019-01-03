## Day 1 of 100 days of code challenge

This is not only day 1 of the 100 days of code challenge, but my first day of using Github and first blog post!

### Math challenge

This is a coding challenge, calling for taking two number arguements - a/b - and adding all numbers inbetween them including themselves. If a = b, then simply return either or; the function should as well account for negative numbers. I did this in Python:

```markdown
def sum_nums(a , b):
    if a == b:
        return a
    if a < b:
         while a != b:   
            for x in range(a+1,b+1):
                a+=x
            return a
    if a > b:
        while b != a:
            for x in range(b+1,a+1):
                b+=x
            return b
```

I ran the code with both positive and negative integers, and it seems to compute correctly. I am decently sure this may be cleaned up a bit, and the syntax seems a bit barbaric, but it works!
Now, to figure out how to do multiple days and become familiar with Github...

Until next time!
