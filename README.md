def add_expense(expenses):
    description = input("Enter expense description: ").strip()

    try:
        amount = float(input("Enter expense amount: ").strip())
    except ValueError:
        print("Invalid amount. Please enter a number.")
        return

    expenses.append({
        "description": description,
        "amount": amount
    })
    print("Expense added successfully.")


def view_expenses(expenses):
    if not expenses:
        print("No expenses recorded.")
        return

    print("\nExpense Records")
    for index, expense in enumerate(expenses, start=1):
        print(f"{index}. {expense['description']} - Rs. {expense['amount']:.2f}")


def delete_expense(expenses):
    view_expenses(expenses)

    if not expenses:
        return

    try:
        expense_number = int(input("Enter expense number to delete: "))
        removed = expenses.pop(expense_number - 1)
        print(f"Deleted: {removed['description']}")
    except (ValueError, IndexError):
        print("Invalid expense number.")


def view_total(expenses):
    total = sum(expense["amount"] for expense in expenses)
    print(f"Total expenses: Rs. {total:.2f}")


def main():
    expenses = []

    while True:
        print("\n--- Expense Tracker ---")
        print("1. Add Expense")
        print("2. View Expenses")
        print("3. Delete Expense")
        print("4. View Total Expenses")
        print("5. Exit")

        choice = input("Choose an option: ")

        if choice == "1":
            add_expense(expenses)
        elif choice == "2":
            view_expenses(expenses)
        elif choice == "3":
            delete_expense(expenses)
        elif choice == "4":
            view_total(expenses)
        elif choice == "5":
            print("Goodbye!")
            break
        else:
            print("Invalid option. Please try again.")


main()
