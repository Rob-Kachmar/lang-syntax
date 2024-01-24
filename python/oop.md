# Python Object Oriented Concepts

## Fundamentals
- Class and Instantiation
  - ```python
      class Transaction:
          text = ''

      instantiated_instance1 = Transaction()
      instantiated_instance2 = Transaction()
      instantiated_instance1.text = 'Hello'
      instantiated_instance2.text = 'World'
      print(instantiated_instance1.text, instantiated_instance2.text)  # Hello World

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

- Passing By Value VS By Reference
  - ```python
      # This is passing by value and not reference because a string is immutable
      def add_item_by_value(s, item):
          s += item
          print(f"s inside the function: {s}")

      a_str = 'ABC'
      print(a_str)  # ABC
      add_item_by_value(a_str, 'D')  # s inside the function: ABCD
      print(a_str)  # ABC

      # This is passing by reference and not value because a list is mutable
      def add_item_by_reference(lst, item):
          lst.append(item)

      a_lst = ['A', 'B', 'C']
      print(a_lst)  # ['A', 'B', 'C']
      add_item_by_reference(a_lst, 'D')
      print(a_lst)  # ['A', 'B', 'C', 'D']

- Polymorphism
  - ```python
      # Polymorphism in action when a single function knows
      # how to handle different kinds of objects as expected.

      name = "Rob"
      print(len(name))  # 3

      lst = ["apples", "bananas", "oranges", "grapes"]
      print(len(lst))  # 4


## SOLID Principles
- Single Responsibility Principle (SRP)
  - A class should do one thing and therefore it should have only a single reason to change.
  - ```python
      class Transaction:
          def __init__(self, account: str, amount: float):
              self.name = account
              self.amount = amount

          # Not following Single Responsibility, because any change to
          # how we deposit funds will now require a change to
          # the Transaction class.
          def deposit_funds(self, destination_bank: str):
              # TODO: send transaction amount to destination bank
              pass


      # It's better to put the depositing functionality into its own class
      class Depositor:
          def __init__(self, destination_bank: str):
              self.destination_bank = destination_bank

          def deposit_funds(self, transaction: Transaction):
              print(f"Send transaction amount {transaction.amount} to {self.destination_bank}")


      t = Transaction('12345678', 100.00)
      dep = Depositor('Big_Bank')
      dep.deposit_funds(t)
      # Send transaction amount 100.0 to Big_Bank

- Open/Closed Principle (OCP)
  - Classes should be open for extension and closed to modification.
  - ```python
      from abc import ABC, abstractmethod


      class Transaction:
          def __init__(self, account: str, amount: float):
              self.account = account
              self.amount = amount


      class AbstractDeposit(ABC):
          @abstractmethod
          def deposit_format(self):
              pass


      class ACHDeposit(AbstractDeposit):
          def __init__(self, transaction: Transaction):
              self.transaction = transaction

          def deposit_format(self):
              return f"{{ACH_deposit_format: {self.transaction.amount} | {self.transaction.account}}}"


      class WireDeposit(AbstractDeposit):
          def __init__(self, transaction: Transaction):
              self.transaction = transaction

          def deposit_format(self):
              return f"{{Wire_deposit_format: {self.transaction.account} | {self.transaction.amount}}}"


      # Depositor doesn't have to change everytime we add a new transaction type deposit format
      class Depositor:
          def __init__(self, destination_bank: str):
              self.destination_bank = destination_bank

          def deposit_funds(self, deposit: AbstractDeposit):
              print(f"Send {deposit.deposit_format()} to {self.destination_bank}")


      t = Transaction('12345678', 100.00)
      ach_deposit = ACHDeposit(t)
      dep = Depositor('Big_Bank')
      dep.deposit_funds(ach_deposit)
      # Send {ACH_deposit_format: 100.0 | 12345678} to Big_Bank

- Liskov's Substitution Principle (LSP)
  - Classes should be substitutable by instances of their subclasses.
  - Good example from here, repeated below: https://www.pythontutorial.net/python-oop/python-liskov-substitution-principle/
  - ```python
      from abc import ABC, abstractmethod


      class Notification(ABC):
          @abstractmethod
          def notify(self, message):
              pass


      class Email(Notification):
          def __init__(self, email):
              self.email = email

          def notify(self, message):
              print(f'Send "{message}" to {self.email}')


      class SMS(Notification):
          def __init__(self, phone):
              self.phone = phone

          def notify(self, message):
              print(f'Send "{message}" to {self.phone}')


      class NotificationManager:
          def __init__(self, notification):
              self.notification = notification

          def send(self, message):
              self.notification.notify(message)


      if __name__ == '__main__':

          sms_notification = SMS('(408)-888-9999')
          email_notification = Email('john@test.com')

          notification_manager = NotificationManager(sms_notification)
          notification_manager.send('Hello John')
          # Send "Hello John" to (408)-888-9999

          notification_manager.notification = email_notification
          notification_manager.send('Hi John')
          # Send "Hi John" to john@test.com

- Interface Segregation Principle (ISP)
  - Many client-specific interfaces are better than one general-purpose interface.
  - Good explanation from here, repeated below: https://dev.to/revisto/solid-design-principles-learn-the-interface-segregation-principle-j8c
  - BAD example
  - The `Printer` class is trying to be all things for all printers, but there are old printers that can't use all the functionality it is requiring.
  - ```python
      from abc import ABC, abstractmethod


      class Printer(ABC):
          @abstractmethod
          def print(self, document):
              pass

          @abstractmethod
          def fax(self, document):
              pass

          @abstractmethod
          def scan(self, document):
              pass


      class OldPrinter(Printer):
          def print(self, document):
              print(f"Printing {document} in black and white...")

          def fax(self, document):
              raise NotImplementedError("Fax functionality not supported")

          def scan(self, document):
              raise NotImplementedError("Scan functionality not supported")

  - GOOD example
  - ```python
      from abc import ABC, abstractmethod


      class Printer(ABC):
          @abstractmethod
          def print(self, document):
              pass


      class Fax(ABC):
          @abstractmethod
          def fax(self, document):
              pass


      class Scanner(ABC):
          @abstractmethod
          def scan(self, document):
              pass


      class OldPrinter(Printer):
          def print(self, document):
              print(f"Printing {document} in black and white...")


      class NewPrinter(Printer, Fax, Scanner):
          def print(self, document):
              print(f"Printing {document} in color...")

          def fax(self, document):
              print(f"Faxing {document}...")

          def scan(self, document):
              print(f"Scanning {document}...")

- Dependency Inversion Principle (DIP)
  - Classes should depend upon interfaces or abstract classes instead of concrete classes and functions.
  - Good explanation from here, repeated below: https://www.pythontutorial.net/python-oop/python-liskov-substitution-principle/
  - BAD example
  - Violation of Dependency Inversion because the higher level class `App` is heavily dependent on the lower level concrete `FXConverterService` class.
  - ```python
      class FXConverterService:
          def convert(self, from_currency, to_currency, amount):
              print(f'{amount} {from_currency} = {amount * 1.2} {to_currency}')
              return amount * 1.2


      class App:
          def start(self):
              converter = FXConverterService()
              converter.convert('EUR', 'USD', 100)


      if __name__ == '__main__':
          app = App()
          app.start()

  - GOOD example
  - Now the higher level `App` class uses the `CurrencyConverter` abstract class, which allows us to easily switch out the `FXConverterServce` concrete class with an alternative `AlphaConverterService` concrete class.
  - ```python
      from abc import ABC


      class CurrencyConverter(ABC):
          def convert(self, from_currency, to_currency, amount) -> float:
              pass


      class FXConverterService(CurrencyConverter):
          def convert(self, from_currency, to_currency, amount) -> float:
              print('Converting currency using FX API')
              print(f'{amount} {from_currency} = {amount * 1.2} {to_currency}')
              return amount * 1.2


      class AlphaConverterService(CurrencyConverter):
          def convert(self, from_currency, to_currency, amount) -> float:
              print('Converting currency using Alpha API')
              print(f'{amount} {from_currency} = {amount * 1.15} {to_currency}')
              return amount * 1.15


      class App:
          def __init__(self, converter: CurrencyConverter):
              self.converter = converter

          def start(self):
              self.converter.convert('EUR', 'USD', 100)


      if __name__ == '__main__':
          converter = AlphaConverterService()
          app = App(converter)
          app.start()
