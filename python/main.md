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

- Calling dynamic python, code running code
  - ```python
      print(eval('1+2'))
      # 3
      print(eval('sum([1, 2, 3, 4])'))
      # 10

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

- Cast using repr() over str() with decimal numbers in previous Python versions, but seems to be fine in Python 3
  - ```python
      print(str(2.0/11.0))
      # 0.18181818181818182
      print(repr(2.0/11.0))
      # 0.18181818181818182

- Square Root
  - ```python
      import math
      print(math.sqrt(49))
      # 7
      print(math.sqrt(48))
      # 6.928203230275509

- Rounding
  - ```python
      import math

      # Regular rounding rules, rounding up at the halfway mark
      print(round(5.3, 0))  # 5.0
      print(round(5.5, 0))  # 6.0
      print(round(5.8, 0))  # 6.0

      # Floor rounding, always rounding down, truncating the decimals to make it an int
      print(math.floor(5.3))  # 5
      print(math.floor(5.5))  # 5
      print(math.floor(5.8))  # 5

      # Ceiling rounding, always rounding up, truncating the decimals to make it an int
      print(math.ceil(5.3))  # 6
      print(math.ceil(5.5))  # 6
      print(math.ceil(5.8))  # 6

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

- String to  `list`
  - ```python
      s = "abcdefg"
      string_lst = list(s)
      print(string_lst)

      # ['a', 'b', 'c', 'd', 'e', 'f', 'g']

- Sort a string into a `list`
  - ```python
      s = "anagram"
      print(sorted(s))  # ['a', 'a', 'a', 'g', 'm', 'n', 'r']
      t = "nagaram"
      print(sorted(t))  # ['a', 'a', 'a', 'g', 'm', 'n', 'r']


## Time
- Convert minutes into an integer of time
  - NOTE: Assuming minutes are under the total 1440 in a day
  - ```python
      total_minutes = 1240
      t = total_minutes // 60 * 100 + total_minutes % 60
      print(t)  # 2040

      h, m = divmod(total_minutes, 60)
      t2 = h * 100 + m
      print(t2)  # 2040


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


## Switch / Match Case Statement
- Match / Case like Switch / Case in other languages
  - ```python
      a = 404999
      result = ""
      match a:
          case 200:
              result = "OK"
          case 404:
              result = "Not Found"
          case _:
              result = "Congratulations, you've reached the end of the internet."

      print(result)  # Congratulations, you've reached the end of the internet.

      val = 'e'
      result = ""
      match val:
          case 'a' | 'b' | 'c':
              result = "abc"
          case 'd' | 'e' | 'f':
              result = "def"
          case _:
              result = "Some letter greater than 'f'."

      print(result)  # def

      val = 'c'
      lst1 = ['a', 'b', 'c']
      lst2 = ['d', 'e', 'f']
      result = ""
      match val:
          case w if w in lst1:
              result = "abc"
          case w if w in lst2:
              result = "def"
          case _:
              result = "Some letter greater than 'f'."

      print(result)  # abc


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

- Check if an element is in a list
  - ```python
      lst = [1, 2, 3, 4, 5, 6, 7, 8, 9]
      print(8 in lst)
      # True
      print(42 in lst)
      # False

- Getting / Filtering values from a list
  - ```python
      lst = [1, 2, 3, 4, 5, 6, 7, 8, 9]

      # Filtered with List Comprehension
      lst_filtered = [i for i in lst if 5 < i < 8]
      print(lst_filtered)
      # [6, 7]

      # Filtered with Lambda where 'i' is the list item
      lst_filtered = list(filter(lambda i: (5 < i < 8), lst))
      print(lst_filtered)
      # [6, 7]

- Slicing a list
  - ```python
      a = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
      print(a)
      # [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]

      print()
      print(a[::1])  # Get the full list in it's current order
      # [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
      print(a[1::1])  # Get the full list in it's current order, skipping the first item
      # [2, 3, 4, 5, 6, 7, 8, 9, 10]
      print(a[1:5:1])  # Get the list in it's current order, skipping the first item, and stopping at the 5th item
      # [2, 3, 4, 5]
      print(a[-5::1])  # Get the list in it's current order, starting at the 5th to last position and continuing on to the end
      # [6, 7, 8, 9, 10]
      print(a[-6::1])  # Get the list in it's current order, starting at the 6th to last position and continuing on to the end
      # [5, 6, 7, 8, 9, 10]
      print(a[-7::1])  # Get the list in it's current order, starting at the 7th to last position and continuing on to the end
      # [4, 5, 6, 7, 8, 9, 10]
      print(a[::-1])  # Get the full list in reverse order
      # [10, 9, 8, 7, 6, 5, 4, 3, 2, 1]
      print(a[-1::-1])  # Get the full list in reverse order
      # [10, 9, 8, 7, 6, 5, 4, 3, 2, 1]
      print(a[-2::-1])  # Get the full list in reverse order, skipping the last list item
      # [9, 8, 7, 6, 5, 4, 3, 2, 1]
      print(a[-2::-1])  # Get the full list in reverse order, skipping the last list item, and stopping at the 5th item
      # [9, 8, 7, 6, 5, 4, 3, 2, 1]
      print(a[-2:-6:-1])  # Get the full list in reverse order, skipping the last list item, and stopping at the 5th item
      # [9, 8, 7, 6]
      print(a[-2:-7:-1])  # Get the full list in reverse order, skipping the last list item, and stopping at the 6th item
      # [9, 8, 7, 6, 5]
      print(a[-2:-8:-1])  # Get the full list in reverse order, skipping the last list item, and stopping at the 7th item
      # [9, 8, 7, 6, 5, 4]

      print()
      print(a[::2])  # Get the list starting with the first item and jumping/stepping every 2 places for the next item
      # [1, 3, 5, 7, 9]
      print(a[1::2])  # Get the list skipping the first item and jumping/stepping every 2 places for the next item
      # [2, 4, 6, 8, 10]
      print(a[::-2])  # Get the list in reverse starting with the last item and jumping/stepping backwards every 2 places for thhe next item
      # [10, 8, 6, 4, 2]
      print(a[-1::-2])  # Get the list in reverse starting with the last item and jumping/stepping backwards every 2 places for thhe next item
      # [10, 8, 6, 4, 2]
      print(a[-2::-2])  # Get the list in reverse skipping the last item and jumping/stepping backwards every 2 places for thhe next item
      # [9, 7, 5, 3, 1]

      print()
      print(a[::3])
      # [1, 4, 7, 10]
      print(a[1::3])
      # [2, 5, 8]
      print(a[::-3])
      # [10, 7, 4, 1]
      print(a[-1::-3])
      # [10, 7, 4, 1]
      print(a[-2::-3])
      # [9, 6, 3]

- Sorting a list
  - ```python
      lst = [1, 3, 4, 2, 8, 9, 7, 6, 5]
      print(lst)
      # [1, 3, 4, 2, 8, 9, 7, 6, 5]

      # This returns a new sorted list. It doesn't sort the original list
      print()
      print(sorted(lst))
      # [1, 2, 3, 4, 5, 6, 7, 8, 9]
      print(lst)
      # [1, 3, 4, 2, 8, 9, 7, 6, 5]
      print(sorted(lst, reverse=True))
      # [9, 8, 7, 6, 5, 4, 3, 2, 1]

      # This actually sorts the original list.
      lst.sort()
      print()
      print(lst)
      # [1, 2, 3, 4, 5, 6, 7, 8, 9]
      lst.sort(reverse=True)
      print(lst)
      # [9, 8, 7, 6, 5, 4, 3, 2, 1]

- Sorting a dictionary by value
  - ```python
      d = {"acct1": 1, "acct2": 2, "acct3": 0, "acct4": 5, "acct5": 0}
      ds = {k: v for k, v in sorted(d.items(), key=lambda i: i[1])}
      print(d)   # {'acct1': 1, 'acct2': 2, 'acct3': 0, 'acct4': 5, 'acct5': 0}
      print(ds)  # {'acct3': 0, 'acct5': 0, 'acct1': 1, 'acct2': 2, 'acct4': 5}

      for k, v in ds.items():
          print(k, v)
      # acct3 0
      # acct5 0
      # acct1 1
      # acct2 2
      # acct4 5

- Sorting objects in a list by their attributes
  - [Sorting in Python](https://wiki.python.org/moin/HowTo/Sorting#Sortingbykeys)
  - ```python
      from operator import attrgetter


      class Person:
          def __init__(self, name: str, age: int, rank=0):
              self.name = name
              self.age = age
              self.rank = rank

          def __repr__(self):
              return f"Person({self.name}, {self.age}, {self.rank})"


      p = [Person('person1', 10, 1), Person('person2', 25, 2),
          Person('person3', 13, 0), Person('person4', 21, 5),
          Person('person5', 45, 0)]

      # We want to sort by rank first in descending order and then by name in ascending order if the ranks match
      print('BEFORE sort:', p)
      ps = [item for item in sorted(p, key=attrgetter('name'))]  # First sort by the secondary sort key
      ps = [item for item in sorted(ps, key=attrgetter('rank'), reverse=True)]  # Then sort by the primary sort key
      print('AFTER sort:', ps)

      BEFORE sort: [Person(person1, 10, 1), Person(person2, 25, 2), Person(person3, 13, 0), Person(person4, 21, 5), Person(person5, 45, 0)]
      AFTER sort: [Person(person4, 21, 5), Person(person2, 25, 2), Person(person1, 10, 1), Person(person3, 13, 0), Person(person5, 45, 0)]

- Copying vs Referencing a List
  - ```python
      original = [1, 2, 3, 4, 5]
      view_reference = original
      actual_copy = original.copy()
      print("original BEFORE update\n\t", original)
      original[2] = 42
      print("original AFTER update\n\t", original)
      print("view_reference\n\t", view_reference)
      print("actual_copy\n\t", actual_copy)

      # original BEFORE update
      #   [1, 2, 3, 4, 5]
      # original AFTER update
      #   [1, 2, 42, 4, 5]
      # view_reference
      #   [1, 2, 42, 4, 5]
      # actual_copy
      #   [1, 2, 3, 4, 5]

- Copying a list without reference
  - ```python
      import copy

      a = [1, 2, 3, 4, 5]
      b = a[:]
      c = a.copy()
      d = copy.deepcopy(a)
      print(a, " -> Original list")
      a[2] = 42
      print(a, "-> Original list updated")
      print(b, " -> Copy of values with a[:] unaffected by update")
      print(c, " -> Shallow copy with a.copy() unaffected by update")
      print(d, " -> Deep copy with copy.deepcopy(a) unaffected by update")
      # [1, 2, 3, 4, 5]  -> Original list
      # [1, 2, 42, 4, 5] -> Original list updated
      # [1, 2, 3, 4, 5]  -> Copy of values with a[:] unaffected by update
      # [1, 2, 3, 4, 5]  -> Shallow copy with a.copy() unaffected by update
      # [1, 2, 3, 4, 5]  -> Deep copy with copy.deepcopy(a) unaffected by update

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

- Inserting between elements in a list
  - ```python
      b = 2
      a = [0, 1, 3]
      a[2:2] = [b]
      print(a)
      # [0, 1, 2, 3]

- Swapping elements in a list
  - ```python
      a = [1, 2, 3, 4]
      print(a)
      # [1, 2, 3, 4]

      # Swap values 3 and 2
      a[1], a[2] = a[2], a[1]
      print(a)
      # [1, 3, 2, 4]

      # Swap back values 3 and 2
      a[2], a[1] = a[1], a[2]
      print(a)
      # [1, 2, 3, 4]

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

- `Sets` and `Lists` unions together
  - ```python
      set1 = {1, 3, 5, 7, 9}
      set2 = {1, 2, 3, 5, 8}
      sets_union = set1 | set2
      print(sets_union)  # {1, 2, 3, 5, 7, 8, 9}

      set1 = {1, 3, 5, 7, 9}
      lst1 = [1, 2, 3, 5, 8]
      # set_union_with_list = set1 | lst1  # TypeError: unsupported operand type(s) for |: 'set' and 'list'
      set_union_with_list = set1.union(lst1)
      print(set_union_with_list)  # {1, 2, 3, 5, 7, 8, 9}

- `Sets` and `Lists` intersecting
  - ```python
      set1 = {1, 3, 5, 7, 9}
      set2 = {1, 2, 3, 5, 8}
      sets_interseting = set1 & set2
      print(sets_interseting)  # {1, 3, 5}

      set1 = {1, 3, 5, 7, 9}
      lst1 = [1, 2, 3, 5, 8]
      # set_interseting_list = set1 & lst1  # TypeError: unsupported operand type(s) for &: 'set' and 'list'
      set_interseting_list = set1.intersection(lst1)
      print(set_interseting_list)  # {1, 3, 5}

- Sum a `list`
  - ```python
      lst = [1, 2, 3, 4, 5]
      print(sum(lst))  # 15

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

- Convert a `list` into a list of tuple pairs, where the value is the key and the original `list` index is the value, and have it sorted by the tuple keys (original values).
  - ```python
      lst = [10, 2, 5, 15, 1, 35, 12]
      print(lst)
      lst = [(value, idx) for idx, value in sorted(enumerate(lst), key=lambda index: index[1])]
      print(lst)

      # [10, 2, 5, 15, 1, 35, 12]
      # [(1, 4), (2, 1), (5, 2), (10, 0), (12, 6), (15, 3), (35, 5)]

- Create a `list` prefilled with None values
  - ```python
      list_elements = 7
      lst = [None] * list_elements
      print(lst)

      # [None, None, None, None, None, None, None]

- DO NOT create a `list` of `lists` like this, because references will be shared
  - ```python
      sub_lists_to_create = 4
      main_list = [[None] * 3] * sub_lists_to_create
      print(main_list)
      # [[None, None, None], [None, None, None], [None, None, None], [None, None, None]]
      main_list[0][0] = 'NEW_VALUE'
      print(main_list)
      # [['NEW_VALUE', None, None], ['NEW_VALUE', None, None], ['NEW_VALUE', None, None], ['NEW_VALUE', None, None]]

- Create a `list` of `lists` with list comprehension where each sublist is independent, without references
  - ```python
      sub_lists_to_create = 4
      main_list = [[None] * 3 for i in range(sub_lists_to_create)]
      print(main_list)
      # [[None, None, None], [None, None, None], [None, None, None], [None, None, None]]
      main_list[0][0] = 'NEW_VALUE'
      print(main_list)
      # [['NEW_VALUE', None, None], [None, None, None], [None, None, None], [None, None, None]]

- Zipping `lists` together
  - NOTE: The final groupings/pairings are limited to the smallest list involved
  - ```python
      a = [1, 2, 3, 4, 5]
      b = ['a', 'b', 'c', 'd', 'e']
      print(list(zip(a, b)))
      # [(1, 'a'), (2, 'b'), (3, 'c'), (4, 'd'), (5, 'e')]

      a = [1, 2, 3, 4, 5]
      b = ['a', 'b', 'c', 'd']
      c = ['x', 'y', 'z']
      print(list(zip(a, b, c)))
      # [(1, 'a', 'x'), (2, 'b', 'y'), (3, 'c', 'z')]

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

- Use map to convert a string of numbers into a list of integers
  - ```python
      s = '123456789'
      m = map(int, str(s))
      # after iterating over it, it becomes empty
      print([i for i in m])  # [1, 2, 3, 4, 5, 6, 7, 8, 9]
      # now this returns 0 because it is empty
      print(sum(m))

      m = map(int, str(s))
      # if we map it again, then we can get the sum()
      print(sum(m))


## Heaps
- Creating a heap with the smallest element at the start
- NOTE: Heaps are not thread-safe.
  - ```python
      import heapq

      lst = [3, 7, 9, 4, 2, 1, 6]
      print(lst)  # [3, 7, 9, 4, 2, 1, 6]
      heapq.heapify(lst)
      # Now the smallest element is at the beginning
      print(lst)  # [1, 2, 3, 4, 7, 9, 6]

- Adding to a heap
  - If you're adding an element that will be the smallest, then it goes to the front, otherwise it's added wherever.
  - ```python
      import heapq

      lst = [3, 7, 9, 4, 2, 1, 6]
      print(lst)  # [3, 7, 9, 4, 2, 1, 6]
      heapq.heapify(lst)
      print(lst)  # [1, 2, 3, 4, 7, 9, 6]
      heapq.heappush(lst, 2)
      print(lst)  # [1, 2, 3, 2, 7, 9, 6, 4]
      heapq.heappush(lst, 5)
      print(lst)  # [1, 2, 3, 2, 7, 9, 6, 4, 5]
      heapq.heappush(lst, 0)
      print(lst)  # [0, 1, 3, 2, 2, 9, 6, 4, 5, 7]
      heapq.heappush(lst, -5)
      print(lst)  # [-5, 0, 3, 2, 1, 9, 6, 4, 5, 7, 2]

- Removing from a heap
  - The function `heapq.heappop()` will remove the smallest element and then readjust to get the next smallest element to the front of the heap.
  - ```python
      import heapq

      lst = [3, 7, 9, 4, 2, 1, 6]
      print(lst)  # [3, 7, 9, 4, 2, 1, 6]
      heapq.heapify(lst)
      print(lst)  # [1, 2, 3, 4, 7, 9, 6]
      heapq.heappop(lst)
      print(lst)  # [2, 4, 3, 6, 7, 9]

- Get n smallest or largest items from the heap
  - ```python
      import heapq

      lst = [3, 7, 9, 4, 2, 1, 6]
      print(lst)  # [3, 7, 9, 4, 2, 1, 6]
      heapq.heapify(lst)
      print(lst)  # [1, 2, 3, 4, 7, 9, 6]
      print(heapq.nsmallest(3, lst))  # [1, 2, 3]
      print(heapq.nlargest(3, lst))  # [9, 7, 6]


## Deque
- Aka Doubly Ended Queue, which is more efficient when appending and popping items from both ends of a list, using time complexity 0(1) vs a list which has a time complexity of 0(n).
  - ```python
      from collections import deque

      # Create a queue
      queue = deque([3, 7, 5, 9, 4, 9, 2, 1, 6])
      print(queue)  # deque([3, 7, 5, 9, 4, 9, 2, 1, 6])

      # Add to the end of the queue
      queue.append(5)
      print(queue)  # deque([3, 7, 5, 9, 4, 9, 2, 1, 6, 5])
      queue.extend([7, 8, 9])
      print(queue)  # deque([3, 7, 5, 9, 4, 9, 2, 1, 6, 5, 7, 8, 9])

      # Add to the start of the queue
      queue.appendleft(8)
      print(queue)  # deque([8, 3, 7, 5, 9, 4, 9, 2, 1, 6, 5, 7, 8, 9])
      queue.extendleft([1, 2, 3])
      print(queue)  # deque([3, 2, 1, 8, 3, 7, 5, 9, 4, 9, 2, 1, 6, 5, 7, 8, 9])

      # Remove from the end of the queue
      queue.pop()
      print(queue)  # deque([3, 2, 1, 8, 3, 7, 5, 9, 4, 9, 2, 1, 6, 5, 7, 8])

      # Remove from the start of the queue
      queue.popleft()
      print(queue)  # deque([2, 1, 8, 3, 7, 5, 9, 4, 9, 2, 1, 6, 5, 7, 8])

      # Count the occurrences of a certain element
      print(queue.count(9))  # 2

      # Get the index of the first occurrence of a certain element
      print(queue.index(9))  # 6
      # Get the index of the first occurrence of a certain element after a certain start
      print(queue.index(9, 6))  # 6
      print(queue.index(9, 7))  # 8

      # Remove the first occurrence of a certain element
      queue.remove(9)
      print(queue)  # deque([2, 1, 8, 3, 7, 5, 4, 9, 2, 1, 6, 5, 7, 8])


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

- for loop through a dictionary to get it's key / value pairs
  - ```python
      dct = {1: 2, 3: 4, 5: 6, "7": 8, 9: "10"}
      for k, v in dct.items():
          print(f"Key: {k} -> Value: {v}")

- for loop through a range
  - ```python
      for i in range(10):
          print(i, end=" | ")

      # 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 |

- for loop through a range in reverse
  - ```python
      for i in reversed(range(10)):
          print(i, end=" | ")

      # 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |


## NumPy
- REFERENCE: [NumPy: the absolute basics for beginners](https://numpy.org/devdocs/user/absolute_beginners.html)
- Create NumPy arrays filled in various ways
  - ```python
      import numpy as np

      # Filled with zeros
      arr = np.zeros(2)
      print(arr)
      # [0. 0.]

      # Filled with zeros in a 3 x 3 matrix
      arr = np.zeros([3, 3])
      print(arr)
      # [[0. 0. 0.]
      #  [0. 0. 0.]
      #  [0. 0. 0.]]

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

- Deleting from a NumPyArray
  - NOTE: numpy.delete() returns a new array
  - ```python
      import numpy as np

      arr = np.arange(1, 10, 1)
      print(arr)
      # [1 2 3 4 5 6 7 8 9]
      indexes_to_remove = [1, 3, 6]  # Numbers: 2, 4, 7
      arr2 = np.delete(arr, indexes_to_remove)
      print(arr2)

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

- Getting / Filtering Values from a NumPy Array
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

- Aggregating NumPy Arrays
  - ```python
      import numpy as np

      b = np.array([[1,2,3], [4,5,6], [7,8,9]])
      print(b)
      # [[1 2 3]
      #  [4 5 6]
      #  [7 8 9]]

      # Y = axis 0 for this 2-D array
      # X = axis 1 for this 2-D array
      #      x ------>
      # y      0  1  2
      # |  0 [[1  2  3]
      # |  1  [4  5  6]
      # V  2  [7  8  9]]

      # NOTE: axis 0 represents the vertical y-axis intersection for the sub arrays, each column
      #       across the sub arrays is evaluated with the sum function.
      print(np.sum(b, axis=0))
      # [12 15 18]
      print(b.sum(axis=0))  # same thing, instead using the built in sum() of the array
      # [12 15 18]

      # NOTE: axis 1 represents the horizontal x-axis, so each sub array is evaluated individually
      #       with the sum function.
      print(b.sum(axis=1))
      # [ 6 15 24]

      # ERROR: since there is no axis above 1 in an array of dimension 2
      # print(b.sum(axis=2))


      # NOTE: For a 1-D array, the only row/list is axis 0
      b = np.array([1,2,3,4,5,6,7,8,9])
      print("\n", b)
      # [1 2 3 4 5 6 7 8 9]

      print(b.sum(axis=0))
      # 45

      # ERROR: since there is no axis above 0 in an array of dimension 1
      # print(b.sum(axis=1))


      b = np.array([[1,2,3,4], [5,6,7,8], [9,10,11,12], [13,14,15,16]])
      print(b)
      # [[ 1  2  3  4]
      #  [ 5  6  7  8]
      #  [ 9 10 11 12]
      #  [13 14 15 16]]

      print("\n", 'MEAN (Average)')
      print(b.mean(axis=0))
      # [ 7.  8.  9. 10.]
      print(b.mean(axis=1))
      # [ 2.5  6.5 10.5 14.5]

      print("\n", 'MIN')
      print(b.min(axis=0))
      # [1 2 3 4]
      print(b.min(axis=1))
      # [ 1  5  9 13]

      print("\n", 'MAX')
      print(b.max(axis=0))
      # [13 14 15 16]
      print(b.max(axis=1))
      # [ 4  8 12 16]

      print("\n", 'MEDIAN (middle of the sequence)')
      print(np.median(b, axis=0))
      # [ 7.  8.  9. 10.]
      print(np.median(b, axis=1))
      # [ 2.5  6.5 10.5 14.5]

- Cummulative Sum in NumPy Arrays
  - ```python
      import numpy as np

      a = np.array([[1,2,3], [4,5,6], [7,8,9]])
      print(a)
      # [[1 2 3]
      #  [4 5 6]
      #  [7 8 9]]

      # Y = axis 0 for this 2-D array
      # X = axis 1 for this 2-D array
      #      x ------>
      # y      0  1  2
      # |  0 [[1  2  3]
      # |  1  [4  5  6]
      # V  2  [7  8  9]]

      print()  # Do a cumulative sum from left-to-right, top-to-bottom for all the arrays
      # with no axis specified for 2-D arrays
      b = np.cumsum(a)
      print(b)
      # [ 1  3  6 10 15 21 28 36 45]

      print()  # Do a cumulative sum from top-to-bottom, across the arrays by column with axis=0 for 2-D arrays
      b = np.cumsum(a, axis=0)
      print(b)
      # [[ 1  2  3]
      #  [ 5  7  9]
      #  [12 15 18]]

      print()  # Do a cumulative sum from left-to-right for each array with axis=1 for 2-D arrays
      b = np.cumsum(a, axis=1)
      print(b)
      # [[ 1  3  6]
      #  [ 4  9 15]
      #  [ 7 15 24]]

- Concatenating NumPy Arrays
  - ```python
      import numpy as np

      a = np.array([[1,1,1], [2,2,2], [3,3,3]])
      b = np.array([[7,7,7], [8,8,8], [9,9,9]])

      print(a)
      # [[1 1 1]
      #  [2 2 2]
      #  [3 3 3]]
      print(b)
      # [[7 7 7]
      #  [8 8 8]
      #  [9 9 9]]

      # Y = axis 0 for this 2-D array
      # X = axis 1 for this 2-D array
      #      x ------>
      # y      0  1  2
      # |  0 [[1  1  1]
      # |  1  [2  2  2]
      # V  2  [3  3  3]]

      # Stacking the array rows with axis 0 for a 2-D array
      print("\n", np.concatenate([a, b], axis=0))
      # [[1 1 1]
      #  [2 2 2]
      #  [3 3 3]
      #  [7 7 7]
      #  [8 8 8]
      #  [9 9 9]]

      # Combining each row with axis 1 for a 2-D array
      print("\n", np.concatenate([a, b], axis=1))
      # [[1 1 1 7 7 7]
      #  [2 2 2 8 8 8]
      #  [3 3 3 9 9 9]]


      # NOTE: For a 1-D array, the only row/list is axis 0
      a = np.array([1,1,1,2,2,2,3,3,3])
      b = np.array([7,7,7,8,8,8,9,9,9])

      print("\n\n")
      print(a)
      # [1 1 1 2 2 2 3 3 3]
      print(b)
      # [7 7 7 8 8 8 9 9 9]

      c = np.concatenate([a, b], axis=0)
      print("\n", c)
      # [1 1 1 2 2 2 3 3 3 7 7 7 8 8 8 9 9 9]

- Flattening NumPy Arrays
  - ```python
      import numpy as np

      a = np.array([[1,2,3], [4,5,6], [7,8,9]])
      print(a)
      # [[1 2 3]
      #  [4 5 6]
      #  [7 8 9]]

      # Use flatten or ravel to combine all the arrays horizontally, left-to-right, with the 'C' ordering
      print("\n")
      print(a.flatten(order='C'))
      print(a.ravel(order='C'))
      # [1 2 3 4 5 6 7 8 9]
      # [1 2 3 4 5 6 7 8 9]

      # Use flatten or ravel to combine all the arrays vertically, then left-to-right with the 'F' ordering
      print("\n")
      print(a.flatten(order='F'))
      print(a.ravel(order='F'))
      # [1 4 7 2 5 8 3 6 9]
      # [1 4 7 2 5 8 3 6 9]


      # As you can see, flatten and ravel work similar, so why both?
      # Well let's update one of our array values after assign and see
      f = a.flatten(order='C')
      r = a.ravel(order='C')
      f[0] = 42
      print("\n")
      print(a)
      # [[1 2 3]
      #  [4 5 6]
      #  [7 8 9]]
      print(f)
      # [42  2  3  4  5  6  7  8  9]


      # Okay, that's what I would expect, nothing happens to the original 'a' array
      # Now, let's update the ravel array 'f'
      r[4] = 42
      print("\n")
      print(a)
      # [[ 1  2  3]
      #  [ 4 42  6]
      #  [ 7  8  9]]
      print(r)
      # [ 1  2  3  4 42  6  7  8  9]

      # And now you see it. The index 4 change in the ravel view is reflected
      # for the same element in the original array.

      # Assigning the ravel result to a variable creates a "view", which
      # is just another way of viewing the same data from the original array.

      # Assigning the flatten result to a variable creates a "copy", which
      # will behave independently of the original array used to created it.

- Using numpy.apply_along_axes to total columns (axes)
  - REFERENCE: [numpy.apply_along_axes](https://numpy.org/doc/stable/reference/generated/numpy.apply_over_axes.html)
  - ```python
      import numpy as np

      def my_func(a):
          """Average first and last element of a 1-D array"""
          print(a)
          return (a[0] + a[-1]) * 0.5


      b = np.array([[1,2,3], [4,5,6], [7,8,9]])
      print(b)
      # [[1 2 3]
      #  [4 5 6]
      #  [7 8 9]]

      # Y = axis 0 for this 2-D array
      # X = axis 1 for this 2-D array
      #      x ------>
      # y      0  1  2
      # |  0 [[1  2  3]
      # |  1  [4  5  6]
      # V  2  [7  8  9]]

      # NOTE: axis 0 represents the vertical y-axis intersection for the sub arrays, each column
      #       across the sub arrays is evaluated with the my_func passed in.
      c = np.apply_along_axis(my_func, 0, b)
      # [1 4 7]
      # [2 5 8]
      # [3 6 9]
      print(c)
      # [4. 5. 6.]

      # NOTE: axis 1 represents the horizontal x-axis, so each sub array is evaluated individually
      #       with the my_func passed in.
      c = np.apply_along_axis(my_func, 1, b)
      # [1 2 3]
      # [4 5 6]
      # [7 8 9]
      print(c)
      # [2. 5. 8.]

      # ERROR: since there is no axis above 1 in an array of dimension 2
      # c = np.apply_along_axis(my_func, 2, b)


      # NOTE: For a 1-D array, the only row/list is axis 0
      b = np.array([1,2,3,4,5,6,7,8,9])
      print("\n", b)
      # [1 2 3 4 5 6 7 8 9]
      c = np.apply_along_axis(my_func, 0, b)
      # [1 2 3 4 5 6 7 8 9]
      print(c)
      # 5.0

      # ERROR: since there is no axis above 0 in an array of dimension 1
      # c = np.apply_along_axis(my_func, 1, b)


      # What if we change the 1-D array into a 2-D array by surrounding it with double brackets
      b = np.array([[1,2,3,4,5,6,7,8,9]])
      print("\n", b)
      # [1 2 3 4 5 6 7 8 9]
      c = np.apply_along_axis(my_func, 0, b)
      # [1]
      # [2]
      # [3]
      # [4]
      # [5]
      # [6]
      # [7]
      # [8]
      # [9]
      print(c)
      # [1. 2. 3. 4. 5. 6. 7. 8. 9.]

      c = np.apply_along_axis(my_func, 1, b)
      # [1 2 3 4 5 6 7 8 9]
      print(c)
      # [5.]


      b = np.array([[8,1,7], [4,3,9], [5,2,6]])
      print("\n", b)
      # [[8 1 7]
      #  [4 3 9]
      #  [5 2 6]]

      # NOTE: axis 0 represents the vertical y-axis intersection for the sub arrays, each column
      #       across the sub arrays is evaluated with the sorted function passed in.
      c = np.apply_along_axis(sorted, 0, b)
      print(c)
      # [[4 1 6]
      #  [5 2 7]
      #  [8 3 9]]

      # NOTE: axis 1 represents the horizontal x-axis, so each sub array is evaluated individually
      #       with the sorted function passed in.
      c = np.apply_along_axis(sorted, 1, b)
      print(c)
      # [[1 7 8]
      #  [3 4 9]
      #  [2 5 6]]


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


# Useful Sites
- [Python Tutorial](https://www.pythontutorial.net/)
  - Excellent resource with clear, easy to understand examples
- [NumPy](https://numpy.org/doc/stable/index.html)
  - Everything you need to know about NumPy. Although, not always the best when it comes to tutorials and examples
- [Sharp Sight](https://www.sharpsightlabs.com/)
  - Great, easy to understand tutorials and examples in the blog.
