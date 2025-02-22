# Alt-School-Project-1
Expense Tracker
A simple Python library for managing financial expenses. This project provides two main classes: Expense for representing individual expenses and ExpenseDB for managing a collection of expenses.

Features
Create and update individual expenses with unique IDs, titles, amounts, and timestamps.
Store and manage a collection of expenses with methods to add, remove, and retrieve expenses by ID or title.
Export expenses to dictionary format for easy serialization or display.
Installation
Prerequisites: Ensure you have Python 3.6 or higher installed.
Clone or Download: Clone this repository or download the source code.
bash
Wrap
Copy
git clone <repository-url>
cd expense-tracker
Dependencies: This project uses only Python's standard library (uuid and datetime), so no additional packages are required.
Usage
Here’s an example of how to use the Expense and ExpenseDB classes:

python
Wrap
Copy
from expense import Expense, ExpenseDB

# Create an ExpenseDB instance
db = ExpenseDB()

# Create some expenses
expense1 = Expense("Groceries", 50.25)
expense2 = Expense("Rent", 1200.00)

# Add expenses to the database
db.add_expense(expense1)
db.add_expense(expense2)

# Update an expense
expense1.update(title="Supermarket", amount=55.00)

# Retrieve and print all expenses
print("All expenses:", db.to_dict())

# Find an expense by ID
found_expense = db.get_expense_by_id(expense2.id)
print("Found expense:", found_expense.to_dict())

# Find expenses by title
groceries = db.get_expense_by_title("Supermarket")
print("Supermarket expenses:", [exp.to_dict() for exp in groceries])

# Remove an expense
db.remove_expense(expense1.id)
print("After removal:", db.to_dict())
Example Output
All expenses: [
    {'id': '123e4567-e89b-12d3-a456-426614174000', 'title': 'Supermarket', 'amount': 55.0, ...},
    {'id': '987fcdeb-1234-5678-9abc-def012345678', 'title': 'Rent', 'amount': 1200.0, ...}
]
Found expense: {'id': '987fcdeb-1234-5678-9abc-def012345678', 'title': 'Rent', 'amount': 1200.0, ...}
Supermarket expenses: [{'id': '123e4567-e89b-12d3-a456-426614174000', 'title': 'Supermarket', 'amount': 55.0, ...}]
After removal: [{'id': '987fcdeb-1234-5678-9abc-def012345678', 'title': 'Rent', 'amount': 1200.0, ...}]
Classes
Expense
Represents an individual financial expense.

Attributes
id (str): A unique identifier (UUID).
title (str): The title of the expense.
amount (float): The amount of the expense.
created_at (datetime): UTC timestamp of creation.
updated_at (datetime): UTC timestamp of the last update.
Methods
__init__(title: str, amount: float): Initializes a new expense.
update(title: str = None, amount: float = None): Updates the title and/or amount, refreshing updated_at.
to_dict() -> dict: Returns a dictionary representation of the expense.
ExpenseDB
Manages a collection of Expense objects.

Attributes
expenses (list): A list storing Expense instances.
Methods
__init__(): Initializes an empty expense collection.
add_expense(expense: Expense): Adds an expense to the collection.
remove_expense(expense_id: str) -> bool: Removes an expense by ID; returns True if successful, False if not found.
get_expense_by_id(expense_id: str) -> Expense | None: Retrieves an expense by ID, or None if not found.
get_expense_by_title(title: str) -> list[Expense]: Retrieves all expenses with the given title.
to_dict() -> list[dict]: Returns a list of dictionaries representing all expenses.
Project Structure
expense-tracker/
├── expense.py    # Contains Expense and ExpenseDB classes
├── README.md     # This file
└── example.py    # Optional: Example usage script
Contributing
Feel free to submit issues or pull requests if you’d like to contribute! Suggestions for improvements (e.g., persistence to a file or database, additional features) are welcome.

License
This project is licensed under the MIT License. See the LICENSE file for details (if applicable).
