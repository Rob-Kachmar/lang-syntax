# Python Object Oriented Concepts

- Class
  - ```python
      class Transaction:
          print("This is my transaction class.")

      # The print statement is called when the class is instantiated
      t1 = Transaction()  # This is my transaction class.

- Class Properties - getters and setters
  - ```python
      class Transaction:
          def __init__(self, account: str, amount: float):
              # assign to internal variables
              self.__account = account
              self.__amount = amount

          # Use the @property decorator for getting read-only attributes
          @property
          def account(self):
              return self.__account

          # Use the @[property_name].setter to externally set its value
          @account.setter
          def account(self, value):
              if len(value) == 0 or len(value) > 17:
                  raise Exception(f"The account '{value if value else 'None'}' length is not between 1 and 17 characters.")
              else:
                  self.__account = value


      t1 = Transaction('12345678', 100)

      print(f"t1.account: {t1.account}")  # t1.account: 12345678

      t1.account = ''  # Exception: The account  length is not between 1 and 17 characters.

- Methods
  - ```python
      class Transaction:
          account = '12345678'
          amount = '200'
          def show_detail(self):
              print(f"account: {self.account} | amount: {self.amount}")

      t1 = Transaction()
      t1.show_detail()  # account: 12345678 | amount: 200

- Inheritance
  - ```python
      class Transaction:
          account = '12345678'
          amount = 1.01

      class ACH(Transaction):
          account = '87654321'

      t1 = Transaction()
      print(t1.account, "|", t1.amount)  # 12345678 | 1.01
      a1 = ACH()
      print(a1.account, "|", a1.amount)  # 87654321 | 1.01

- Constructor
  - ```python
      class Transaction:
          def __init__(self, account: str, amount: float):
              # assign to internal variables
              self.account = account
              self.amount = amount

      # t1 = Transaction()  # Fails for missing two required parameters of the constructor
      t1 = Transaction('135791113', 1.11)
      print(t1.account, "|", t1.amount)  # 135791113 | 1.11

- Overload
  - Python docs: [singledispatch](https://docs.python.org/3.4/library/functools.html#functools.singledispatch)
  - ```python
      from functools import singledispatch

      @singledispatch
      def add_something(arg):
          return 1 + arg

      @add_something.register(str)
      def _(arg):
          return 'S' + arg

      print(add_something(9))  # 10
      print(add_something('t r i n g'))  # St r i n g

- Abstract Class
  - ```python
      from abc import ABC, abstractmethod

      class Transaction(ABC):
          @abstractmethod
          def show_transaction_type(self):
              pass

          @property
          @abstractmethod
          def transaction_type(self):
              pass

          @property
          @abstractmethod
          def amount(self):
              pass

          @amount.setter
          @abstractmethod
          def amount(self, value):
              pass

      class ACH(Transaction):
          def __init__(self, amount):
              self.__amount = amount

          def show_transaction_type(self):
              print("I am an ACH")

          @property
          def transaction_type(self):
              return 'ACH'

          @property
          def amount(self):
              return self.__amount

          @amount.setter
          def amount(self, value):
              self.__amount = value

      class Wire(Transaction):
          def __init__(self, amount):
              self.__amount = amount

          def show_transaction_type(self):
              print("I am a Wire")

          @property
          def transaction_type(self):
              return 'Wire'

          @property
          def amount(self):
              return self.__amount

          @amount.setter
          def amount(self, value):
              self.__amount = value


      t = ACH(1.01)
      print("transaction_type:", t.transaction_type)  # transaction_type: ACH
      t.show_transaction_type()  # I am an ACH
      print("t.amount:", t.amount)  # 1.01
      t.amount = 2.01
      print("t.amount:", t.amount)  # 2.01
      t = Wire(1.02)
      print("transaction_type:", t.transaction_type)  # transaction_type: Wire
      t.show_transaction_type()  # I am a Wire
      print("t.amount:", t.amount)  # 1.02
      t.amount = 2.02
      print("t.amount:", t.amount)  # 2.02

- Polymorphism
  - ```python
      # Polymorphism in action when a single function knows
      # how to handle different kinds of objects as expected.

      name = "Rob"
      print(len(name))  # 3

      lst = ["apples", "bananas", "oranges", "grapes"]
      print(len(lst))  # 4
