# Comparison Operators

In several cases, you'll have multiple instances of any given data type, and you'll need to compare one of them to another. The simplest way to do so is with `comparison operators`, which look at the two values of each instance and return a boolean depending on what relationship you're looking for. The most obvious use case is with numbers, as they have the most straightforward and easily quantifiable values. Comparison operators will determine if one value is more, less, or equal to another value:

```py
1 == 1 # True
1 > 2 # False
2 < 1 # True
3 >= 2 # True
4 <= 1 # False
5 != 5 # False
```

Two things to note when checking for equality, you need to use double equal signs, as the single equal sign declares a value (1 == 1 checks for equality, 1 = 1 tries to make a variable called "1" with a value of 1). The other thing is the exclaimation point, which in Python is a way of indication "not" (1 != 2 means "one is not equal to two").

Strings can also be compared to each other by using a handful of miscellaneous processes, such as alphabetical order, or capital letters being greater than lowercase letters, and so on. But what about comparisons between a string and a number?

```py
print("hello" > 3)

# Traceback (most recent call last):
#   File "/home/markbjohns/comparison_ops/app.py", line 1, in <module>
#     print("hello" > 3)
# TypeError: '>' not supported between instances of 'str' and 'int'
```

While floats and integers are technically different data types, they can be compared because they are both numbers, and they are the exeception. As a general rule, two different data types cannot be compared to each other, as there's no way to compare the value of data type "x" in direct relation to the value of data type "y". Here are all the comparators you'll see and what they're referring to:

| Comparator | Meaning |
|:-----------|:--------|
| `<` | Strictly less than |
| `<=` | Less than or equal |
| `>` | Strictly greater than |
| `>=` | Greater than or equal |
| `==` | Equal |
|`!=` | Not equal |

## Boolean Operators

In addition to basic comparisons, you can combine multiple state checks to return a single boolean, useful for when you need several conditions to pass or when there are multiple acceptable conditions.

The `and` boolean operator looks at two booleans and returns "True" if both of them are true. You can create those booleans programmatcally and Python will compare them after they're generated.

```py
True and True # True

True & False # False

1 > 3 and 2 != 9 # False

2 < 5 & 7 == 7 # True
```

The `or` operator, instead of checking that both values are true, will check if a single value is true.

```py
False or True # True

False or False # False

1 > 5 or 6 < 10 # True

2 != 2 or 4 > 3 # False
```

The final boolean operator, which we've already seen is `not`, which just negates whatever boolean it's applied to. Just like double negatives cancelling each other out, this can make the False boolean True as well as making the True boolean False.

```py
not True # False

not False # True
```

This works differently with NumPy arrays. Say we have a NumPy array of bmi calculations, we can use the regular operators to find all the values that match a condition.

```py
bmi = np.array([21.852, 20.975, 21.75, 24.747, 21.441])

bmi > 21
# array([True, False, True, True, True], dtype=bool)

bmi < 22
# array([True, True, True, False, True], dtype=bool)
```

If you try to use a boolean comparison, it will just return an error:

```py
bmi > 21 and bmi < 22

# ValueError: The truth value of an array with more than one element is ambiguous. Use a.any() or a.all()
```

In order to use boolean operators with NumPy, we have methods built in, `logical_and()`, `logical_or()`, and `logical_not()`. This works the same way as the boolean operators, but uses a function call instead of using the operators directly. You can also use it on the array directly with brackets to get the actual values instead of booleans:

```py
np.logical_and(bmi > 21, bmi < 22)

# array([True, False, True, False, True], dtype=bool)

bmi[np.logical_and(bmi > 21, bmi < 22)]

# array([21.852, 21.75, 21.441])
```
