#Dino
import random
def print_row(row):
    print("------------------------")
    print(" | ".join(row))
    print("------------------------")
def spin_row():
    emote = ["🎄", "🤶🏻", "🎅", "🦖", "🐗"]
    return [random.choice(emote) for _ in range(3)]
def get_payout(row , bet):
    if row[0] == row[1] == row[2]:
        if row[0] == '🎄':
            return bet*3
        elif row[0] == '🤶🏻':
            return bet*6
        elif row[0] == '🎅':
            return bet*8
        elif row[0] == '🦖':
            return bet*10
        elif row[0] == '🐗':
            return bet*30
    return 0
def main():
    balance = 100
    print("--------------------------------")
    print("WELCOME TO OUR SPINNING GAME")
    print("SYMBOLS :🎄 🤶🏻 🎅 🦖 🐗 ")
    print("--------------------------------")
    while balance > 0:
        print(f"Current balance: ${balance}")
        bet = input("Enter your bet amount: ")
        if not bet.isdigit():
            print("Please enter a valid number")
            continue
        bet = int(bet)
        if bet > balance:
            print("Insufficient funds")
            continue
        if bet <= 0 :
            print("Bet must be positive")
            continue
        balance -= bet
        row = spin_row()
        import time
        print("Spinning...")
        for x in range(1,4):
            time.sleep(1)
            print(x)
        print_row(row)

        payout = get_payout(row , bet)
        if payout > 0:
            print(f"You won ${payout}")
        else:
            print(f"You lost ${bet}")
        balance += payout

        play_again = input("Do you want to play again? (y/n): ").lower()
        if play_again == "n":
            break
        else:
            continue
    print("------------------------------------------------")
    print(f"GAME OVER! Your current balance is ${balance}")
    print("------------------------------------------------")
if __name__ == '__main__':
    main()
