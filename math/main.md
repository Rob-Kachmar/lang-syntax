# Math Essentials for Programming

# Logarithms
  - You're trying to determine what power you need to raise a base number to in order to get another. You're basically taking the inverse of an exponent.
    - 2^3 two to the power of three is the same as 2 * 2 * 2 = 8
    - 3^3 three to the power of three is the same as 3 * 3 * 3 = 27
    - 2^4 two to the power of four is the same as 2 * 2 * 2 * 2 = 16
  - Now inverting the approach to determine the log(n)
    - log(8) for a base 2 is the same as 8 / 2 / 2 / 2 = 1, so log(8) = 3 for base 2
    - log(27) for a base 3 is the same as 27 / 3 / 3 / 3 = 1, so log(27) = 3 for base 3
    - log(16) for a base 2 is the same as 16 / 2 / 2 / 2 / 2, so log(16) = 4 for base 2


# Permutations
  - You're getting all the unique combinations of the items in a list. In some lotteries, your numbers are 1 to 75, but that's more complicated than we'll cover here, since order doesn't matter. Unless specified with a permutation problem, order does matter.
    - For example, to get all the permutations of 3 from [x, y, z] you have 6 possibilities:
      - x, y, z
      - x, z, y
      - y, x, z
      - y, z, x
      - z, x, y
      - z, y, x
  - The formula is 3 * 2 * 1 = 6. Meaning, you first start of with 3 choices, then you only have 2 more choices, and finally you have 1 choice.
  - Written another way as a factorial of n:
    - 3! = 3 * 2 * 1 = 6, so there are 6 ways of arranging 3 diffenent items in a 3 item list
    - 4! = 4 * 3 * 2 * 1 = 24, so there are 24 ways of arranging 4 different items in a 4 item list
    - 5! = 5 * 4 * 3 * 2 * 1 = 120, so there are 120 ways of arranging 5 different items in a 5 item list


# Subsets
  - These can either be none, some, or all of the elements of a larger set of items. For these, order does not matter.
    - For example, ['a', 'c', 'f'] is a subset of ['a', 'b', 'c', 'd', 'e', 'f']
  - The formula works out to be 2^n possible subsets, because you have the choice of including or excluding each element
    - For the list [1], you have 2^1, or 2 possibilities: [], [1]
    - For the list [1, 2], you have 2^2, or 4 possibilities: [], [1], [2], [1, 2]
    - For the list [1, 2, 3], you have 2^3 or 8 possibilities: [], [1], [2], [3] [1, 2], [1, 3], [2, 3], [1, 2, 3]


# Arithmetic sequence
  - If a sequence of numbers always increase by the same number, then it is an arithmetic sequence.
    - For example, [1, 2, 3, 4, 5, 6, 7] is an arithmetic sequence, because 1+1 = 2, 2+1 = 3, ..., 6+1 = 7, so you're always increasing by 1 to get to the next number in the sequence
    - This example, [1, 2, 5, 6] is not because 1+1 = 2, but 2+1 does not equal 5, so you're not always increasing by the same number to get to the next number in the sequence.
  - The formula for the sum works out to be (first_item + last_item) * total_items / 2, so for the list [1, 2, 3, 4, 5, 6, 7]
    - (1 + 7) * 7 / 2 = 28
    - 1 + 2 + 3 + 4 + 5 + 6 + 7 = 28
    - Imagine if your list went on for 1,000,000 or 10^6 items, this is where you need those formulas. :-)


# Geometric sequence
  - If a sequence of numbers always has the same ratio between each of the numbers, then it is a geometric sequence.
    - [1, 2, 4, 8, 16] --> [1, 2] is 1:2 or 2/1=2, [2, 4] is 1:2 or 4/2=2, [4, 8] is 1:2 or 8/4=2, [8, 16] is 1:2 or 16/8=2
    - [1, 3, 9, 27, 81] --> [1, 3] is 1:3 or 3/1=3, [3, 9] is 1:3 or 9/3=3, [9, 27] is 1:3 or 27/9=3, [27, 81] is 1:3 or 81/27=3
  - The formula for the sum is: first_item * (1 - ratio^total_items) / (1 - ratio), so for the list [1, 2, 4, 8, 16]
    - 1 * (1 - 2^5) / (1 - 2) = 31
    - 1 + 2 + 4 + 8 + 16 = 31
    - Again, imagine if your list went on for 1,000,000 or 10^6 items, the formula comes in to save you.


# Modulo
  - Getting the modulo is like a form of division where you are just interested in the remainder, and most programming languages express the operator as a % sign.
    - Let's say you have 9 / 3, you get 3 with no remainder, so 9 % 3 would give you 0 for no remainder.
    - Let's say you have 11 / 5, you get 2 with a 1/5 remainer, so 11 % 5 would give you 1 for the 1 that 5 could not fully divide
    - Let's say you have 12 / 5, you get 2 with a 2/5 remainer, so 12 % 5 would give you 2 for the 2 that 5 could not fully divide
    - Let's say you have 13 / 5, you get 2 with a 3/5 remainer, so 13 % 5 would give you 3 for the 3 that 5 could not fully divide
    - Let's say you have 14 / 5, you get 2 with a 4/5 remainer, so 14 % 5 would give you 4 for the 4 that 5 could not fully divide
    - Which also means that anytime the number being divided (dividend) is less than the number dividing (divisor), it will always be the dividend.
    - 1 / 3 gives you a 1/3 remainer, so 1 % 3 would give you 1 for the 1 that 3 could not fully divide
    - 2 / 3 gives you a 2/3 remainer, so 2 % 3 would give you 2 for the 2 that 3 could not fully divide
  - If you are determining if an integer (n) is prime
    - NOTE: Prime numbers have 2 and only 2 divisors, themselves and 1. 1 is not a prime number because it only has 1 divisor
    - That leaves a range of 2 to (n - 1), or starting with 2 until the number just before the number (n) you are evaluating, because you already know the number is divisible by 1 and itself. You're just trying to figure out if it is divisible by any other numbers, which would exclude it from being prime.
    - You can reduce that range significantly by taking the square root of n, because any non-prime number will have another divisor between 2 and it's square root.
      - Pseudo Code/Formula: if (i % 2) = 0 for the range(2, sqrt(n)), then not prime
      - For n = 15, the range is 2 - 3, 15 % 2 = 1 and 15 % 3 = 0, so it can't be prime, because it is divisible by 1, 3, and 15, more than 2 divisors
        - NOTE: The square root of 15 is 3.something, but since we're working with integers, we just lop off the decimals and get 3
      - For n = 17, the range is 2 - 4, 17 % 2 = 0, 17 % 3 = 0, and 17 % 4 = 0, so it is prime, because it is not divisible by any other numbers than 1 and 17, only 2 divisors.
        - NOTE: The square root of 17 is 4.something, but since we're working with integers, we just lop off the decimals and get 4

# REFERENCES:
- [AlgoMonster - Math for Technical Interviews](https://algo.monster/problems/math-basics)
