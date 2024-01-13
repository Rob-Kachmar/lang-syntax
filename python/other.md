# Other Python Language Techniques

- Rotate a matrix 90 degrees
  - ```python
      import numpy

      mtrx = [[1, 2, 3],
          [4, 5, 6],
          [7, 8, 9]]

      print(numpy.rot90(mtrx, -1))

- Unique pair combinations in an array, ignoring ordering difference repetition
  - i.e. (1,2) is the same as (2,1), just in a different order
  - ```python
      a = [1, 2, 3, 4]
      # Brute force
      combos = [(a[0], a[1]), (a[0], a[2]), (a[0], a[3]), (a[1], a[2]), (a[1], a[3]), (a[2], a[3])]
      print(combos)
      # [(1, 2), (1, 3), (1, 4), (2, 3), (2, 4), (3, 4)]

      # List Comprehension
      # NOTE: The sorting is not optimal, just useful to show the output is the same with above.
      combos = sorted([(j, i) for ix, i in enumerate(a) for jx, j in enumerate(a) if ix > jx])
      print(combos)
      # [(1, 2), (1, 3), (1, 4), (2, 3), (2, 4), (3, 4)]

- Finding Anagrams
  - ```python
      from collections import Counter
      lst = ["ears", "aa", "eras", "bb", "cc", "sear"]

      # Filtered with List Comprehension
      lst_filtered = [i for i in lst if Counter(i) == Counter("ares")]
      print()
      print(lst_filtered)
      # ['ears', 'eras', 'sear']
      lst_filtered = [i for i in lst if sorted(i) == sorted("ares")]
      print(lst_filtered)
      # ['ears', 'eras', 'sear']

      # Filtered with Lambda
      print()
      lst_filtered = list(filter(lambda i: Counter(i) == Counter("ares"), lst))
      print(lst_filtered)
      # ['ears', 'eras', 'sear']
      lst_filtered = list(filter(lambda i: sorted(i) == sorted("ares"), lst))
      print(lst_filtered)
      # ['ears', 'eras', 'sear']

- Finding Palindromes
  - ```python
      lst = ["ears", "deed", "eras", "wow", "rotator", "racecar", "peer"]

      # Filtered with List Comprehension
      lst_filtered = [i for i in lst if i == "".join(reversed(i))]
      print()
      print(lst_filtered)
      # ['deed', 'wow', 'rotator', 'racecar']

      # Filtered with Lambda
      print()
      lst_filtered = list(filter(lambda i: i == "".join(reversed(i)), lst))
      print(lst_filtered)
      # ['deed', 'wow', 'rotator', 'racecar']

- Slice a list in contiguous segments walking through 1 at a time
  - ```python
      lst = [1, 2, 3, 4, 5, 6, 7]
      sub_size = 4

      # Basic Looping
      for i in range(len(lst) - sub_size + 1):
          print(lst[i:i+sub_size])
      # [1, 2, 3, 4]
      # [2, 3, 4, 5]
      # [3, 4, 5, 6]
      # [4, 5, 6, 7]

      # List Comprehension
      new_lst = [lst[i:i+sub_size] for i in range(len(lst) - sub_size + 1) if len(lst[i:i+sub_size]) == sub_size]
      print(new_lst)
      # [[1, 2, 3, 4], [2, 3, 4, 5], [3, 4, 5, 6], [4, 5, 6, 7]]
