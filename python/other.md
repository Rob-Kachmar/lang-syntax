# Other Python Language Techniques

* Rotate a matrix 90 degrees
  * ```python
      import numpy

      mtrx = [[1, 2, 3],
          [4, 5, 6],
          [7, 8, 9]]

      print(numpy.rot90(mtrx, -1))
