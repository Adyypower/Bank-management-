class Bank:
    def __init__(self):
        self.name = ""
        self.address = ""
        self.acc_type = ""
        self.balance = 0
        self.password = ""

    def get_password(self):
        from getpass import getpass
        return getpass("Enter password: ")

    def valid_password(self):
        input_password = self.get_password()
        if input_password == self.password:
            return True
        else:
            print("Invalid password")
            return False

    def account_open(self):
        self.name = input("Enter Account holder name: ")
        self.address = input("Enter your Address: ")
        self.acc_type = input("Account Type (S for Saving, A for Active): ")
        self.password = self.get_password()

    def deposit(self):
        if self.valid_password():
            amount = int(input("Enter Amount to deposit: "))
            self.balance += amount
            print(f"Your Balance is: {self.balance}")
        else:
            print("You entered an invalid password!")

    def display(self):
        if self.valid_password():
            print(f"Account holder name: {self.name}")
            print(f"Address: {self.address}")
            print(f"Account type: {self.acc_type}")
            print(f"Balance: {self.balance}")
        else:
            print("You entered an invalid password!")

    def withdraw(self):
        if self.valid_password():
            amount = int(input("Enter Amount to Withdraw: "))
            if amount > self.balance:
                print("Insufficient balance!")
            else:
                self.balance -= amount
                print(f"Your Balance is: {self.balance}")
        else:
            print("You entered an invalid password!")


def main():
    bank = Bank()

    while True:
        print("\nWelcome to Aditya Bank")
        print("Choose your Operation:")
        print("1. Open Account")
        print("2. Deposit")
        print("3. Display Account Info")
        print("4. Withdraw")
        print("5. Exit")

        choice = int(input("Enter your choice: "))
        if choice == 1:
            bank.account_open()
        elif choice == 2:
            bank.deposit()
        elif choice == 3:
            bank.display()
        elif choice == 4:
            bank.withdraw()
        elif choice == 5:
            print("Thank you for using Aditya Bank!")
            break
        else:
            print("Invalid choice, please choose between 1 to 5.")

if __name__ == "__main__":
    main()
