# python_prj
Built a banking system using Object-Oriented Programming concept, Implemented deposit,  withdrawal, interest &amp; overdraft features.and Applied Encapsulation, Inheritance, Polymorphism,  Abstraction. 
 class BankAccount:
    def __init__(self, account_no, name, balance):
        self.account_no = account_no
        self.name = name
        self.balance = balance

    def deposit(self, amount):
        self.balance += amount
        print(amount, "deposited. New balance:", self.balance)

    def withdraw(self, amount):
        if amount <= self.balance:
            self.balance -= amount
            print(amount, "withdrawn. Remaining balance:", self.balance)
        else:
            print("Insufficient balance!")

    def display_details(self):
        print("Account No:", self.account_no)
        print("Name:", self.name)
        print("Balance:", self.balance)

    def calculate_benefit(self):
        pass

class SavingsAccount(BankAccount):
    def __init__(self, account_no, name, balance, interest_rate):
        super().__init__(account_no, name, balance)
        self.interest_rate = interest_rate

    def calculate_benefit(self):
        interest = self.balance * self.interest_rate / 100
        print("Interest for Savings Account:", interest)
        return interest

class CurrentAccount(BankAccount):
    def __init__(self, account_no, name, balance, overdraft_limit):
        super().__init__(account_no, name, balance)
        self.overdraft_limit = overdraft_limit

    def calculate_benefit(self):
        print("Overdraft limit available:", self.overdraft_limit)
        return self.overdraft_limit

def add_balances(acc1, acc2):
    return acc1.balance + acc2.balance

s_account = SavingsAccount(101, "Vijay", 5000, 5)
c_account = CurrentAccount(102, "Ravi", 3000, 1000)

s_account.display_details()
c_account.display_details()

s_account.deposit(2000)
c_account.withdraw(500)

s_account.calculate_benefit()
c_account.calculate_benefit()

print("Total balance of both accounts:", add_balances(s_account, c_account))

