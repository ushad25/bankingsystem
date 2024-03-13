# bankingsystem

import random #This line imports the random module, which is used later to generate a random account number.
accounts = {} #This dictionary will store information about each account
def create_account()#This function prompts the user to enter their name and initial balance. It generates a random account number and creates a new entry in the accounts dictionary with this information.
    name = input("Enter your name: ")
    initial_balance = float(input("Enter initial balance: "))
    account_number = random.randint(1000, 9999)

    accounts[account_number] = {
        'name': name,
        'balance': initial_balance
    }

    print(f"Account created successfully! Your account number is {account_number}")


def login():#This function allows a user to log in by entering their account number. If the account number exists in the accounts dictionary, it prints a welcome message; otherwise, it prompts the user to try again.
    account_number = int(input("Enter your account number: "))

    if account_number in accounts:
        print(f"Welcome, {accounts[account_number]['name']}!")
        return account_number
    else:
        print("Invalid account number. Please try again.")
        return None


def deposit(account_number):#This function allows a logged-in user to deposit money into their account. It prompts the user to enter the deposit amount and updates the account balance accordingly.
    amount = float(input("Enter the deposit amount: "))

    if amount > 0:
        accounts[account_number]['balance'] += amount
        print(f"Deposit successful. New balance: {accounts[account_number]['balance']}")
    else:
        print("Invalid amount for deposit.")


def withdraw(account_number):#Similar to the deposit function, this function allows a logged-in user to withdraw money from their account, provided the withdrawal amount is valid and there is enough balance.
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
        if account_number is not None:#Menu Options:

                                                      
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

 # The menu options include:
                                                       # Create Account (Choice 1): Calls the create_account function.
                                                       # Login (Choice 2): Calls the login function and, if successful, displays a sub-menu for account-related actions.
                                                       # Deposit (Choice 3): Prints a message to login first.
                                                        #Withdraw (Choice 4): Prints a message to login first.
                                                        #Exit (Choice 5): Exits the program.

       

