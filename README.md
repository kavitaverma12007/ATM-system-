# ATM SYSTEM #
Mini ATM project 
import openpyxl

name = ""
acc_no = 0
balance = 0
transactions = []

pin = input("Enter your PIN: ")

def menu():
    print("\n==== ATM SYSTEM ====")
    print("1. Create Account")
    print("2. Deposit Money")
    print("3. Withdraw Money")
    print("4. Show Balance")
    print("5. Exit")


def new_acc():
    global name, acc_no, balance

    name = input("Enter your name: ")
    acc_no = int(input("Enter account number: "))
    balance = int(input("Enter balance: "))

    transactions.append(["Create Account", balance, balance])
    print("Account created successfully!")


def deposit():
    global balance

    amount = int(input("Enter deposit amount: "))
    balance = balance + amount

    transactions.append(["Deposit", amount, balance])
    print("Money deposited successfully!")


def withdraw():
    global balance

    amount = int(input("Enter withdrawal amount: "))

    if amount <= balance:
        balance = balance - amount
        transactions.append(["Withdraw", amount, balance])
        print("Please collect your cash.")
    else:
        print("Insufficient balance!")


def show_balance():
    print("Name:", name)
    print("Account No:", acc_no)
    print("Balance:", balance)


def save_excel():
    wb = openpyxl.Workbook()
    ws = wb.active

    ws.append(["Account No", "Name", "Transaction", "Amount", "Balance"])

    for t in transactions:
        ws.append([acc_no, name, t[0], t[1], t[2]])

    wb.save("ATM.xlsx")
    print("Excel file saved successfully!")
    
if pin == pin:
    while True:
        menu()
        choice = int(input("Enter your choice: "))

        if choice == 1:
            new_acc()

        elif choice == 2:
            deposit()

        elif choice == 3:
            withdraw()

        elif choice == 4:
            show_balance()

        elif choice == 5:
            save_excel()
            print("Thank you!")
            break

        else:
            print("Invalid choice!")
