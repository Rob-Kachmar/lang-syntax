# Python Language Syntax Reference

## Basics
- Function
  - ```python
      def my_function(param):
          return f"param: {param}"


      print(my_function("Hello World!"))

      # param: Hello World!

- Calling a function with named parameters
  - ```python
      def divide_numbers(dividend, divisor):
          return dividend / divisor


      print(f"quotient = {divide_numbers(dividend=10, divisor=2)}")

      # quotient = 5.0

- Working with True, False, and None (Null)
  - ```python
      result = True
      print(f"result: {result}")

      result = False
      print(f"result: {result}")

      v = None
      result = (v is None)
      print(f"v: {v} | result of '(v is None)': {result}")

      v = None
      result = not (v is None)
      print(f"v: {v} | result of 'not (v is None)': {result}")

      # result: True
      # result: False
      # v: None | result of '(v is None)': True
      # v: None | result of 'not (v is None)': False

- Check if a string is a digit
  - ```python
      n = '1'
      print(f"n.isdigit(): {n.isdigit()}")
      print(f"n: {n} is{'' if n.isdigit() else ' not'} a digit.")
      n = 'a'
      print(f"n.isdigit(): {n.isdigit()}")
      print(f"n: {n} is{'' if n.isdigit() else ' not'} a digit.")

      # n.isdigit(): True
      # n: 1 is a digit.
      # n.isdigit(): False
      # n: a is not a digit.

- Casting a numeric string into a number and back into a string
  - NOTE: Only put it in a list so the output would be obvious as to being an integer or a string.
  - ```python
      n = ['1']
      if n[0].isdigit():
          n = [int(n[0])]
          print(n)
          n = [str(n[0])]
          print(n)

      # [1]
      # ['1']

## Operators
- Shortcut operators +=, -=, **=
  - ```python
      count = 10
      print(f"count: {count}")
      count += 2
      print(f"Incrementing count by 2: {count}")
      count -= 2
      print(f"Decrementing count by 2: {count}")
      count **= 2
      print(f"Raising count to the power of 2: {count}")

      # count: 10
      # Incrementing count by 2: 12
      # Decrementing count by 2: 10
      # Raising count to the power of 2: 100

- Shortcut operators /=, *=
  - NOTE: Division (/) always changes an integer into a decimal
  - ```python
      count = 10
      print(f"count: {count}")
      count /= 2
      print(f"Dividing count by 2: {count}")
      count *= 2
      print(f"Multiplying count by 2: {count}")

      # count: 10
      # Dividing count by 2: 5.0
      # Multiplying count by 2: 10.0

- Floor Division with shortcut operator //=
  - NOTE: Floor Division (//) always gives an integer, dropping any decimals
  - ```python
      count = 10
      print(f"count: {count}")
      count //= 2
      print(f"Floor Division of count by 2: {count}")
      count //= 2
      print(f"Floor Division of count, again by 2: {count}")
      count //= 3
      print(f"Floor Division of count by 3: {count}")

      # count: 10
      # Floor Division of count by 2: 5
      # Floor Division of count, again by 2: 2
      # Floor Division of count by 3: 0

- Modulo with shortcut operator %=
  - NOTE: Modulo (%) will always give the remainder of a division, dropping any whole numbers.
  - ```python
      count = 20
      print(f"count: {count}")
      count %= 3
      print(f"Modulo of count by 3: {count}")
      count %= 3
      print(f"Modulo of count, again by 3: {count}")
      count %= 1
      print(f"Modulo of count by 1: {count}")

      # count: 20
      # Modulo of count by 3: 2
      # Modulo of count, again by 3: 2
      # Modulo of count by 1: 0


## Strings
- Concatenating strings
  - ```python
      s1 = 'Hello'
      s2 = 'World'
      s3 = "!"
      result = s1 + s2 + s3
      print(result)
      result = " ".join([s1, s2, s3])
      print(result)
      result = f"{s1} {s2}{s3}"
      print(result)

      # HelloWorld!
      # Hello World !
      # Hello World!

- Does a substring exist in a string
  - ```python
      s = 'This is my string.'
      sub = 'str'
      if sub in s:
          print(f"The substring '{sub}' is in 's': {s}")

      # The substring 'str' is in 's': This is my string.

- Replace a subtring in a string
  - ```python
      s = 'This is my string.'
      sub = 'str'
      new_sub = 'STR'
      print(s.replace(sub, new_sub))

      # This is my STRing.

- Splitting a string with a delimiter (defaults to a blank space).
  - ```python
      s = 'This is my string.'
      print(f"s: {s}")
      lst = s.split()
      print(f"Splitting a string with no delimiter:\n\t{lst}")
      lst = s.split(' ')
      print(f"Splitting a string with a ' '(space) delimiter:\n\t{lst}")
      lst = s.split('i')
      print(f"Splitting a string with 'i' as the delimiter:\n\t{lst}")

      # s: This is my string.
      # Splitting a string with no delimiter:
      #     ['This', 'is', 'my', 'string.']
      # Splitting a string with a ' '(space) delimiter:
      #     ['This', 'is', 'my', 'string.']
      # Splitting a string with 'i' as the delimiter:
      #     ['Th', 's ', 's my str', 'ng.']

- Splitting with a regex
  - ```python
      import re
      s = "pop hello_world (p1) : (p2, p3) this is cool"
      lst = re.split(r'[ ,)(:]', s)
      print(lst)

      # ['pop', 'hello_world', '', 'p1', '', '', '', '', 'p2', '', 'p3', '', 'this', 'is', 'cool']

- Get the last segment of a file name (file type), splitting on '.'
  - ```python
      file = 'my-very.cool-document__..__.txt'
      file_type = file.split(".")[-1]
      print(file_type)

      # txt

- Stripping leading and trailing spaces and/or other characters
  - ```python
      s = "       ,  text to keep,"
      print (f"String to strip leading an trailing characters:\n\t{s}")
      final = s.strip()
      print(f"Just strip out leading and trailing spaces:\n\t{final}")
      final = s.strip(",")
      print(f"Just strip out leading and trailing commas:\n\t{final}")
      final = s.strip(" ,")
      print(f"Strip out leading and trailing spaces and commas:\n\t{final}")

      # String to strip leading an trailing characters:
      # 	       ,  text to keep,
      # Just strip out leading and trailing spaces:
      # 	,  text to keep,
      # Just strip out leading and trailing commas:
      # 	       ,  text to keep
      # Strip out leading and trailing spaces and commas:
      # 	text to keep

- String slicing syntax [[start:stop:step]](https://docs.python.org/3/library/functions.html#slice)
- Get only the first two characters. `start` is blank for starting at the beginning, and `stop` is 2 to stop after 2 characters.
  - ```python
      s = "abcdef"[:2]
      print(s)

      # ab

- Get only the last two characters. `start` is -2 for starting at the last 2 characters, and `stop` is blank for continuing on for the remainder of the string.
  - ```python
      s = "abcdef"[-2:]
      print(s)

      # ef

- Skip the first two characters.  `start` is 2 for starting after the first 2 characters, and `stop` is blank for continuing on for the remainder of the string.
  - ```python
      s = "abcdef"[2:]
      print(s)

      # cdef

- Skip the last two characters.  `start` is blank for starting at the beginning, and `stop` is -2 for stopping before the last 2 characters.
  - ```python
      s = "abcdef"[:-2]
      print(s)

      # abcd

- Skip the first and last two characters. `start` is 2 for starting after the first 2 characters, and `stop` is -2 for stopping before the last 2 characters.
  - ```python
      s = "abcdef"[2:-2]
      print(s)

      # cd

- Reverse a string. `start` and `stop` are blank so the whole string is captured, and `step` is -1 so it is traversed from the end to the beginning.
  - ```python
      s = "abcdef"[::-1]
      print(s)

      # fedcba

- Ensure you always get a two digit month with leading zeros.
  - ```python
      month = 1
      month_2 = str(month + 100)[-2:]
      print(month_2)

      # 01

- String to List
  - ```python
      s = "abcdefg"
      string_lst = list(s)
      print(string_lst)

      # ['a', 'b', 'c', 'd', 'e', 'f', 'g']


## If Statments
- Basic if statement
  - ```python
      if 1 == 1:
        print("1 equals 1")

      # 1 equals 1

- Basic if else statement
  - ```python
      if 1 == 2:
        pass
      else:
        print("1 does not equal 2")

      # 1 equals 1

- Basic else if statement
  - ```python
      if 1 == 2:
        pass
      elif 2 == 2:
        print("2 equals 2")
      else:
        print("1 does not equal 2")

      # 2 equals 2

- Ternary operator or one-line if statement
  - ```python
      s = "2 equals 2" if 2 == 2 else "How did you get here?"
      print(s)

      # 2 equals 2


## Lists, Sets, and Dictionaries
- Get the length of a `list`
  - ```python
      lst = [1, 2, 3, 4, 5]
      print(f"len(lst): {len(lst)}")

      # len(lst): 5

- Create a linked list and add a couple of values
  - ```python
      import collections
      linked_lst = collections.deque()
      linked_lst.append(1)
      linked_lst.append(2)
      print(list(linked_lst))

      # [1, 2]

- Adding (appending) and removing (deleting) from a `list`
  - NOTE: After removing an element from a list, all the indexes change from that element onward!
  - ```python
      lst = [1, 2, 3, 4, 5]
      print(f"lst: {lst}")
      lst.append(6)
      print(f"Append to the end of a list: {lst}")
      del(lst[0])
      print(f"Delete the first element of a list: {lst}")
      lst.pop(2)
      print(f"Pop out / remove the 3rd element of a list: {lst}")
      lst.pop()
      print(f"Pop out / remove the last element of a list: {lst}")

      # lst: [1, 2, 3, 4, 5]
      # Append to the end of a list: [1, 2, 3, 4, 5, 6]
      # Delete the first element of a list: [2, 3, 4, 5, 6]
      # Pop out / remove the 3rd element of a list: [2, 3, 5, 6]
      # Pop out / remove the last element of a list: [2, 3, 5]

- Replacing (overwriting) a `list` element by index
  - ```python
      lst = [1, 2, 3, 4, 5]
      print(f"lst: {lst}")
      lst[2] = 999
      print(f"Replacing the 3rd element in a list: {lst}")

      # lst: [1, 2, 3, 4, 5]
      # Replacing the 3rd element in a list: [1, 2, 999, 4, 5]

- Remove all the blank, space-only, and None elements from a list
  - ```python
      lst = [1, '', '', 2, '', 3, 4, '', ' ', '', None, 5]
      print(f"BEFORE: {lst}")
      lst = [v for v in lst if str(v).strip() != '' and not (v is None)]
      print(f"AFTER: {lst}")

      # BEFORE: [1, '', '', 2, '', 3, 4, '', ' ', '', None, 5]
      # AFTER: [1, 2, 3, 4, 5]

- Turn a `list` into a `set` to remove any duplicates. However, the ```set``` has no defined ordering and will output the items in an indeterminate order every time.
  - ```python
      lst = ['a', 'a', 'b', 'b', 'b', 'c', 'd', 'd', 'e', 'f']
      print(f"lst as a list: {lst}")
      lst = set(lst)
      print(f"lst as a set: {lst}")

      # lst as a list: ['a', 'a', 'b', 'b', 'b', 'c', 'd', 'd', 'e', 'f']
      # lst as a set: {'f', 'c', 'b', 'e', 'a', 'd'}

- Sum a `list`
  - ```python
      lst = [1, 2, 3, 4, 5]
      print(sum(lst))

      # 15

- Aggregate a `list` by element value and their counts into a `dict` (dictionary / hash table) of the results.
    - ```python
      lst = ['a', 'a', 'b', 'b', 'b', 'c', 'd', 'd', 'e', 'f']
      agg_dict = dict(map(lambda k: (k, lst.count(k)), lst))
      print(agg_dict)

      # {'a': 2, 'b': 3, 'c': 1, 'd': 2, 'e': 1, 'f': 1}

- Aggregate a `list` by element value and their counts into a `list` of tuples.
    - ```python
      import itertools
      lst = ['a', 'a', 'b', 'b', 'b', 'c', 'd', 'd', 'e', 'f']
      agg_dict = [(k, len(list(g))) for k, g in itertools.groupby(sorted(lst))]
      print(agg_dict)

      # [('a', 2), ('b', 3), ('c', 1), ('d', 2), ('e', 1), ('f', 1)]

- Aggregate a `list` by element value and their counts into an `OrderedDict` (ordered dictionary / hash table) of the results.
  - NOTE: I haven't found a faster way than this.
  - ```python
      import collections
      from collections import Counter
      lst = ['a', 'a', 'b', 'b', 'b', 'c', 'd', 'd', 'e', 'f']
      agg_dict = collections.OrderedDict(sorted(Counter(lst).items()))
      print(agg_dict)

      # OrderedDict([('a', 2), ('b', 3), ('c', 1), ('d', 2), ('e', 1), ('f', 1)])

- Convert a `list` into a list of tuple pairs, where the value is the key and the original `list` index is the value, and have it sorted by the tuple keys.
  - ```python
      lst = [10, 2, 5, 15, 1, 35, 12]
      print(lst)
      lst = [(value, idx) for idx, value in sorted(enumerate(lst), key=lambda index: index[1])]
      print(lst)

      # [10, 2, 5, 15, 1, 35, 12]
      # [(1, 4), (2, 1), (5, 2), (10, 0), (12, 6), (15, 3), (35, 5)]

- Create a `list` of `lists` with list comprehension
  - ```python
      sub_lists_to_create = 7
      main_list = [[] for i in range(sub_lists_to_create)]
      print(main_list)

      # [[], [], [], [], [], [], []]

- Create a `list` prefilled with None values
  - ```python
      list_elements = 7
      lst = [None] * list_elements
      print(lst)

      # [None, None, None, None, None, None, None]

- Adding (appending) and removing (deleting) from a `dict` (dictionary), is done with keys, not with indexes as you would in a `list`.
  - ```python
      dct = {1: 2, 3: 4, 5: 6, "7": 8, 9: "10"}
      print(dct)
      dct[2] = 3
      print(f"Append to the end of the dictionary for the new key of 2:\n\t{dct}")
      dct[3] = 444
      print(f"Update the value of key 3 in the dictionary:\n\t{dct}")
      # del(dct[7])  # this will fail because the 7 key is a string in this dictionary
      # del(dct["1"])  # this will fail because the 1 key is an integer in this dictionary
      del(dct[5])
      print(f"Delete key 5 from the dictionary:\n\t{dct}")

      # {1: 2, 3: 4, 5: 6, '7': 8, 9: '10'}
      # Append to the end of the dictionary for the new key of 2:
      #     {1: 2, 3: 4, 5: 6, '7': 8, 9: '10', 2: 3}
      # Update the value of key 3 in the dictionary:
      #     {1: 2, 3: 444, 5: 6, '7': 8, 9: '10', 2: 3}
      # Delete key 5 from the dictionary:
      #     {1: 2, 3: 444, '7': 8, 9: '10', 2: 3}


## Loopping
- Basic for loop through a list
  - ```python
      lst = [1, 2, 3, 4, 5]
      for i in lst:
          print(f"i: {i}, ", end='')

      # i: 1, i: 2, i: 3, i: 4, i: 5,

- Basic while loop
  - ```python
      lst = [1, 2, 3, 4, 5]
      while len(lst) > 0:
          print(f"{lst.pop()}, ", end='')

      # 5, 4, 3, 2, 1,

- Break out of (short ciruit) a loop
  - ```python
      lst = [1, 2, 3, 4, 5]
      for i in lst:
          if i == 3:
              break
          else:
              print(f"i: {i}, ", end='')

      # i: 1, i: 2,

- for loop in reverse
  - ```python
      lst = [1, 2, 3, 4, 5]
      for i in sorted(lst, reverse=True):
        print(f"i: {i}, ", end='')

      # i: 5, i: 4, i: 3, i: 2, i: 1,

- for loop with a range taken from the length of a list
  - ```python
      lst = [1, 2, 3, 4, 5]
      for i in range(len(lst)):
          print(f"lst[i]: {lst[i]}, ", end='')

      # lst[i]: 1, lst[i]: 2, lst[i]: 3, lst[i]: 4, lst[i]: 5,

- for loop with a range starting at the 3rd element (beginning at index: 2) and getting the next 3 elements (indexes: 2, 3, and 4, stopping just before index 5)
  - ```python
      lst = [10, 9, 8, 7, 6, 5, 4, 3, 2, 1]
      for i in range(2, 5):
          print(f"lst[i]: {lst[i]}, ", end='')

      # lst[i]: 8, lst[i]: 7, lst[i]: 6,

- for loop with enumerate to get the value and its index
  - ```python
      lst = [1, 2, 3]
      for idx, i in enumerate(lst):
          print(f"i: {i} at idx: {idx}, ", end='')

      # : 1 at idx: 0, i: 2 at idx: 1, i: 3 at idx: 2,


## NumPy
- REFERENCE: [NumPy: the absolute basics for beginners](https://numpy.org/devdocs/user/absolute_beginners.html)
- Create NumPy arrays filled in various ways
  - ```python
      import numpy as np

      # Filled with zeros
      arr = np.zeros(2)
      print(arr)
      # [0. 0.]

      # Filled with ones
      arr = np.ones(2)
      print(arr)
      # [1. 1.]

      # Filled with random numbers
      arr = np.empty(2)
      print(arr)
      # [3.14 42.]

      # Filled by a range
      arr = np.arange(4)
      print(arr)
      # [0 1 2 3]

      # Filled by evenly spaced intervals (first number, last number, step size)
      arr = np.arange(2, 9, 2)
      print(arr)
      # [2 4 6 8]

      # Filled with numbers linearly spaced
      arr = np.linspace(0, 10, num=5)
      print(arr)
      # [ 0.   2.5  5.   7.5 10. ]

      # Default data type is np.float64, but you can override it
      arr = np.ones(2, dtype=np.int64)
      print(arr)
      # [1 1]

- Identifying and Reshaping a NumPy Array
  - ```python
      import numpy as np

      arr1 = np.arange(1, 10, 1)
      print(arr1)
      # [1 2 3 4 5 6 7 8 9]

      # Reshaping an array
      arr = arr1.reshape(3, 3)
      print(arr)
      # [[1 2 3]
      #  [4 5 6]
      #  [7 8 9]]

      # Rotating an array
      arr = np.rot90(arr, -1)
      print(arr)
      # [[7 4 1]
      #  [8 5 2]
      #  [9 6 3]]

      # Identify how many dimensions in the array
      print(arr.ndim)
      # 2

      # Identify the shape of the array
      print(arr.shape)
      # (3, 3)

      # Identify the size of the array (product of the shape sides)
      print(arr.size)
      # 9

- Sorting and Concatenating NumPy Arrays
  - ```python
      import numpy as np

      # Sorting an array
      lst = [2, 7, 3, 4, 1, 9, 6, 8, 5]
      arr = np.sort(np.array(lst))
      print(arr)
      # [1 2 3 4 5 6 7 8 9]

      # Concatenating arrays
      arr1 = np.array([1, 2, 3, 4, 5])
      arr2 = np.array([6, 7, 8, 9, 10])
      arr = np.concatenate((arr1, arr2))
      print(arr)
      # [ 1  2  3  4  5  6  7  8  9 10]

      # Concatenating multi-dimensional arrays
      arr1 = np.array([[1, 2], [3, 4]])
      arr2 = np.array([[5, 6]])
      arr = np.concatenate((arr1, arr2), axis=0)
      print(arr)
      # [[1 2]
      #  [3 4]
      #  [5 6]]

- Slicing a NumPy Array, like String slicing
  - ```python
      import numpy as np

      arr = np.arange(6)
      print(arr)
      # [0 1 2 3 4 5]

      # Get the 2nd element
      print(arr[1])
      # 1

      # Get the first 2 elements
      print(arr[:2])
      # [0 1]

      # Skip the 1st element and get the rest
      print(arr[1:])
      # [1 2 3 4 5]

      # Get the last 2 elements
      print(arr[-2:])
      # [4 5]

- Getting values from a NumPy Array
  - ```python
      import numpy as np

      arr = (np.arange(1, 13, 1)).reshape(3, 4)
      print(arr)
      # [[ 1  2  3  4]
      #  [ 5  6  7  8]
      #  [ 9 10 11 12]]

      # Get all the array values < 6
      print(arr[arr < 6])
      # [1 2 3 4 5]

      # Get all the array values >= 5
      print(arr[arr >= 5])
      # [ 5  6  7  8  9 10 11 12]

      # Get elements divisible by 2
      print(arr[arr % 2 == 0])
      # [ 2  4  6  8 10 12]

      # Get elements > 2 and < 11
      print(arr[(arr > 2) & (arr < 11)])
      # [ 3  4  5  6  7  8  9 10]

      # Get elements <= 2 or >= 11
      print(arr[(arr <= 2) | (arr >= 11)])
      # [ 1  2 11 12]


## Vectorizing with NumPy
- REFERENCE: [Replacing Loops with Vectorization](https://dev.to/chamodperera/replacing-for-loops-with-vectorization-in-python-21m6)
- Vectorize a basic for loop
  - ```python
      import numpy as np

      # Regular for loop, multiplying each element by 2
      lst = [1, 2, 3, 4, 5]
      for i in range(len(lst)):
          lst[i] = lst[i] * 2
      print(lst)

      # [2, 4, 6, 8, 10]

      # Vectorizing syntax for the same calculation without looping
      lst = [1, 2, 3, 4, 5]
      np_arr = np.array(lst)
      np_arr = np_arr * 2
      print(list(np_arr))

      # [2, 4, 6, 8, 10]
