# Lambdas in Python

Lambda functions are brief, anonymous functions in Python, ideal for simple, one-time tasks. They are defined by the 
lambda keyword, and they use the following syntax:

```Python
lambda x: expr
```

In the example above, x represents a parameter to be used in the expression expr, and it acts just like any parameter 
in a traditional function. expr is the expression that gets evaluated and returned when the lambda function is called.

## Lambdas and Map

Lambda functions can be valuably combined with the map() function, which executes a specified function for each 
element in a collection of objects, such as a list:

```Python
map(lambda x: x * 2, [1, 2, 3])
```

The function to execute is passed as the first argument, and the iterable is passed as the second argument.

The result of the example above would be [2, 4, 6], where each item in the list passed to map() has been doubled by 
the action of the lambda function.

To obtain a readable output you need to turn the map object into a list. Do it by passing the map() call as the 
argument to the list() function.

## Examples

### Example using lambdas and collections

```Python
def add_expense(expenses, amount, category):
    expenses.append({'amount': amount, 'category': category})


def print_expenses(expenses):
    for expense in expenses:
    print(f'Amount: {expense["amount"]}, Category: {expense["category"]}')


def total_expenses(expenses):
    return sum(map(lambda expense: expense['amount'], expenses))

def filter_expenses_by_category(expenses, category):
    return filter(lambda expense: expense['category'] == category, expenses)


def main():
    expenses = []
    while True:
    print('\nExpense Tracker')
    print('1. Add an expense')
    print('2. List all expenses')
    print('3. Show total expenses')
    print('4. Filter expenses by category')
    print('5. Exit')
    
    choice = input('Enter your choice: ')

        if choice == '1':
            amount = float(input('Enter amount: '))
            category = input('Enter category: ')
            add_expense(expenses, amount, category)

        elif choice == '2':
            print('\nAll Expenses:')
            print_expenses(expenses)
    
        elif choice == '3':
            print('\nTotal Expenses: ', total_expenses(expenses))
    
        elif choice == '4':
            category = input('Enter category to filter: ')
            print(f'\nExpenses for {category}:')
            expenses_from_category = filter_expenses_by_category(expenses, category)
            print_expenses(expenses_from_category)
    
        elif choice == '5':
            print('Exiting the program.')
            break
```