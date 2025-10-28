from datetime import datetime
class Task:
    def __init__(self, title, description, deadline):
        self.title = title
        self.description = description
        self.deadline = deadline
        self.completed = False  # Стан завдання (виконано / не виконано)

    def mark_completed(self):
        self.completed = True

    def __str__(self):
        status = "✅ Виконано" if self.completed else "❌ Не виконано"
        return f"Назва: {self.title}\nОпис: {self.description}\nДедлайн: {self.deadline}\nСтан: {status}\n"

class TaskManager:
    def __init__(self):
        self.tasks = []

    def add_task(self, task):
        self.tasks.append(task)
        print(f"Завдання '{task.title}' додано!")

    def remove_task(self, title):
        for task in self.tasks:
            if task.title == title:
                self.tasks.remove(task)
                print(f"Завдання '{title}' видалено!")
                return
        print(f"Завдання '{title}' не знайдено.")

    def mark_task_completed(self, title):
        for task in self.tasks:
            if task.title == title:
                task.mark_completed()
                print(f"Завдання '{title}' відмічено як виконане!")
                return
        print(f"Завдання '{title}' не знайдено.")

    def show_tasks(self):
        if not self.tasks:
            print("Список завдань порожній.")
        else:
            print("📋 Список завдань:")
            for task in self.tasks:
                print(task)

if __name__ == "__main__":
    manager = TaskManager()

    task1 = Task("Написати звіт", "Підготувати звіт до понеділка", "2025-10-20")
    task2 = Task("Купити продукти", "Молоко, хліб, яйця", "2025-10-18")

    manager.add_task(task1)
    manager.add_task(task2)
    
    manager.show_tasks()

    manager.mark_task_completed("Купити продукти")

    manager.remove_task("Написати звіт")

    manager.show_tasks()
