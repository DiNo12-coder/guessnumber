def show_balanced():
    print(f"Your balance is ${balanced: .2f}")
def deposited():
    amount = float(input("Enter your deposited amount: "))
    if amount <= 0:
        print("Your deposited amount must be positive")
        return 0
    else:
        return amount
def withdrawal():
    amounts = float(input("Enter your withdrawal amount: "))
    if amounts < 0:
        print("Your withdrawal amount must be positive")
        return 0
    elif amounts > balanced:
        print("Your withdrawal amount must be less than your balance")
        return 0
    else:
        print(f"Your were withdraw ${amounts: .2f}")
        return amounts
balanced = 0
is_running = True
while is_running:
    print("--------------------------")
    print("BANKING PROGRAM")
    print("1.show balanced")
    print("2.deposit")
    print("3.withdraw")
    print("4.Exit")
    print("--------------------------")
    choice = input("Enter your choice (1-4):")
    if choice == "1":
        show_balanced()
    elif choice == "2":
        balanced += deposited()
    elif choice == "3":
        balanced -= withdrawal()
    elif choice == "4":
        is_running = False
        break
    else:
        print("Invalid choice!")
        continue
print("Thank you for using this program")
print("Have a nice day!")


if __name__ == "__main__":
    show_balanced()
    deposited()
    withdrawal()
