import matplotlib.pyplot as plt

class BudgetTracker:
    def __init__(self, initial_budget):
        self.initial_budget = initial_budget
        self.remaining_budget = initial_budget
        self.income = 0
        self.expenses = {}

    def add_income(self, amount):
        self.income += amount
        self.remaining_budget += amount

    def add_expense(self, category, amount):
        if category not in self.expenses:
            self.expenses[category] = amount
        else:
            self.expenses[category] += amount
        self.remaining_budget -= amount

    def display_budget_summary(self):
        print("Initial Budget:", self.initial_budget)
        print("Income:", self.income)
        print("Expenses:")
        for category, amount in self.expenses.items():
            print(f"- {category}: {amount}")
        print("Remaining Budget:", self.remaining_budget)

    def visualize_spending(self):
        categories = list(self.expenses.keys())
        amounts = list(self.expenses.values())

        plt.figure(figsize=(8, 5))
        plt.bar(categories, amounts, color='skyblue')
        plt.xlabel('Categories')
        plt.ylabel('Amount')
        plt.title('Spending by Category')
        plt.xticks(rotation=45)
        plt.tight_layout()
        plt.show()

# Example usage
if __name__ == "__main__":
    budget_tracker = BudgetTracker(1000)

    budget_tracker.add_income(2000)
    budget_tracker.add_expense('Groceries', 150)
    budget_tracker.add_expense('Utilities', 100)
    budget_tracker.add_expense('Entertainment', 200)

    budget_tracker.display_budget_summary()
    budget_tracker.visualize_spending()
