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

- Polymorphism
  - ```python
      # Polymorphism in action when a single function knows
      # how to handle different kinds of objects as expected.

      name = "Rob"
      print(len(name))  # 3

      lst = ["apples", "bananas", "oranges", "grapes"]
      print(len(lst))  # 4
