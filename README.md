# bankingsystem

import random
accounts = {}
def create_account():
    name = input("Enter your name: ")
    initial_balance = float(input("Enter initial balance: "))
    account_number = random.randint(1000, 9999)

    accounts[account_number] = {
        'name': name,
        'balance': initial_balance
    }

    print(f"Account created successfully! Your account number is {account_number}")


def login():
    account_number = int(input("Enter your account number: "))

    if account_number in accounts:
        print(f"Welcome, {accounts[account_number]['name']}!")
        return account_number
    else:
        print("Invalid account number. Please try again.")
        return None


def deposit(account_number):
    amount = float(input("Enter the deposit amount: "))

    if amount > 0:
        accounts[account_number]['balance'] += amount
        print(f"Deposit successful. New balance: {accounts[account_number]['balance']}")
    else:
        print("Invalid amount for deposit.")


def withdraw(account_number):
    amount = float(input("Enter the withdrawal amount: "))

    if 0 < amount <= accounts[account_number]['balance']:
        accounts[account_number]['balance'] -= amount
        print(f"Withdrawal successful. New balance: {accounts[account_number]['balance']}")
    else:
        print("Invalid amount for withdrawal or insufficient balance.")


# Main program
while True:
    print("\nBanking System Menu:")
    print("1. Create Account")
    print("2. Login")
    print("3. Deposit")
    print("4. Withdraw")
    print("5. Exit")

    choice = input("Enter your choice (1-5): ")

    if choice == '1':
        create_account()
    elif choice == '2':
        account_number = login()
        if account_number is not None:
            while True:
                print("\nAccount Menu:")
                print("1. Deposit")
                print("2. Withdraw")
                print("3. Logout")

                option = input("Enter your option (1-3): ")

                if option == '1':
                    deposit(account_number)
                elif option == '2':
                    withdraw(account_number)
                elif option == '3':
                    print("Logout successful.")
                    break
                else:
                    print("Invalid option. Please try again.")
    elif choice == '3':
        print("Please login before making a deposit.")
    elif choice == '4':
        print("Please login before making a withdrawal.")
    elif choice == '5':
        print("Exiting the program. Thank you!")
        break
    else:
        print("Invalid choice. Please enter a number between 1 and 5.")



        ![image](https://github.com/ushad25/bankingsystem/assets/162864032/af7896bb-0b79-48f0-8ae5-50cb78451e21)
        ![image](https://github.com/ushad25/bankingsystem/assets/162864032/617698f6-8959-4fe5-b6b1-2c1a90f3edfd)


