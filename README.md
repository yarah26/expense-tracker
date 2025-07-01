

# C++ Console Expense Tracker

A simple, console-based expense and income tracking application written in C++. This program allows users to record their financial transactions, view a history of their records, calculate total spending for a specific month, and save their data to a file for persistence.

## Features

  - **Add Expenses:** Record expenses by selecting a category (Bills, Entertainment, Food, Transportation) and specifying the date and amount.
  - **Add Income:** Record income with a specific date and amount.
  - **View All Records:** Display a complete list of all recorded expenses and income transactions.
  - **Monthly Summary:** Calculate and display the total amount spent in a given month and year.
  - **Data Persistence:** Automatically save all records to a `expenses.txt` file upon exiting and load them back when the application starts.
  - **Dynamic Memory Management:** The application uses dynamic arrays to efficiently manage the list of expenses, resizing as needed.

## Getting Started

### Prerequisites

To compile and run this project, you will need a C++ compiler that supports C++11 or later (for `stod` and `to_string`). Most modern C++ compilers, such as GCC (G++) or Clang, will work.

### Compilation

1.  **Save the Code:** Save the provided source code as a `.cpp` file (e.g., `main.cpp`).

2.  **Open a Terminal:** Navigate to the directory where you saved the file.

3.  **Compile the Program:** Use your C++ compiler to create an executable.

    **Using G++:**

    ```sh
    g++ main.cpp -o expense_tracker
    ```

    **Using Clang:**

    ```sh
    clang++ main.cpp -o expense_tracker
    ```

### Execution

Run the compiled program from your terminal:

```sh
./expense_tracker
```

The program will start and either load existing data from `expenses.txt` or begin with a clean slate.

## How to Use

When you run the application, you will be presented with a main menu:

```
1. Add Expense
2. Add Income
3. View All Records
4. View Total Spent by Month
5. Save & Exit
Choose an option:
```

  - **1. Add Expense:** Prompts you to choose a category, enter a date in `YYYY-MM-DD` format, and provide the amount.
  - **2. Add Income:** Prompts you to enter a date in `YYYY-MM-DD` format and the income amount.
  - **3. View All Records:** Displays all transactions, including date, category, and amount.
  - **4. View Total Spent by Month:** Asks for a year and month in `YYYY-MM` format and calculates the total expenses for that period (excluding income).
  - **5. Save & Exit:** Saves all current records to `expenses.txt` and closes the application.

## File Structure

The application creates and interacts with a single file:

  - `expenses.txt`: A comma-separated values (CSV) file used to store the transaction data. Each line represents a single transaction in the format:
    `YYYY-MM-DD,Category,Amount`

    **Example:**

    ```
    2024-07-28,Food,15.75
    2024-07-29,Income,1200.00
    2024-08-01,Bills,85.50
    ```

## Code Overview

The program is structured into two main classes:

### `Expense` Class

  - **Purpose:** Represents a single financial transaction (either an expense or income).
  - **Attributes:**
      - `category` (string): The category of the transaction (e.g., "Food", "Income").
      - `date` (string): The date of the transaction.
      - `amount` (double): The monetary value.
  - **Key Methods:**
      - `display()`: Prints the transaction details to the console.
      - `toFileString()`: Converts the transaction data into a CSV string for file storage.
      - `fromFileString()`: A static method that parses a CSV string to create an `Expense` object.

### `ExpenseTracker` Class

  - **Purpose:** Manages the collection of all `Expense` objects.
  - **Attributes:**
      - `expenses` (Expense\*\*): A dynamic array of pointers to `Expense` objects.
      - `count` (int): The current number of transactions stored.
      - `capacity` (int): The current allocated size of the dynamic array.
  - **Key Methods:**
      - `addExpense()`: Adds a new transaction, handling negative amount validation and resizing the array if necessary.
      - `viewExpenses()`: Iterates through and displays all stored transactions.
      - `viewTotalSpentByMonth()`: Filters transactions by month and calculates the total spending.
      - `saveToFile()` / `loadFromFile()`: Manages reading from and writing to the `expenses.txt` file.
      - `resize()`: A private helper method to double the capacity of the `expenses` array when it's full.

-----
