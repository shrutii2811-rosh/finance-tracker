# finance-tracker
This project is a lightweight Command Line Interface (CLI) tool designed to help users manage their daily finances. It was developed to demonstrate core Python concepts like File I/O, Data Validation, and Modular Programming.
import csv
from datetime import datetime

def add_expense(amount, category, description):
    date = datetime.now().strftime("%Y-%m-%d %H:%M:%S")
    with open('expenses.csv', 'a', newline='') as file:
        writer = csv.writer(file)
        writer.writerow([date, amount, category, description])
    print("Expense added successfully!")

def view_expenses():
    try:
        with open('expenses.csv', 'r') as file:
            reader = csv.reader(file)
            print("\n--- Your Expenses ---")
            for row in reader:
                print(f"Date: {row[0]} | Amount: {row[1]} | Category: {row[2]} | Note: {row[3]}")
    except FileNotFoundError:
        print("No expenses recorded yet.")

# Simple Menu
while True:
    print("\n1. Add Expense  2. View All  3. Exit")
    choice = input("Choose an option: ")
    if choice == '1':
        amt = input("Enter amount: ")
        cat = input("Enter category (Food/Travel/Etc): ")
        desc = input("Enter description: ")
        add_expense(amt, cat, desc)
    elif choice == '2':
        view_expenses()
    elif choice == '3':
        break

        
