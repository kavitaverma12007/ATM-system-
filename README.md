# ATM-system-
Mini ATM project 
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
    balance = int(input("Enter current balance: "))
    print("Account created successfully!")

def deposit():
    global balance
    amt = int(input("Enter amount to deposit: "))
    balance = balance + amt
    print("Amount deposited successfully!")

def withdraw():
    global balance
    amt = int(input("Enter amount to withdraw: "))
    if balance >= amt:
        balance = balance - amt
        print("Please collect your cash.")
    else:
        print("Insufficient balance!")

def show_balance():
    print("Account Holder:", name)
    print("Current Balance:", balance)

while True:
    menu()
    ch = int(input("Enter your choice: "))

    if ch == 1:
        new_acc()
    elif ch == 2:
        deposit()
    elif ch == 3:
        withdraw()
    elif ch == 4:
        show_balance()
    elif ch == 5:
        print("Thank you!")
        break
    else:
        print("Enter a valid choice!")
        menu()
