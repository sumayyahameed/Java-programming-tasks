# Java-programming-tasks
class TodoList:
    def __init__(self):
        self.tasks = []

    def add_task(self, task):
        self.tasks.append(task)

    def remove_task(self, task):
        if task in self.tasks:
            self.tasks.remove(task)
        else:
            print("Task not found in the list.")

    def view_tasks(self):
        if self.tasks:
            for index, task in enumerate(self.tasks, start=1):
                print(f"{index}. {task}")
        else:
            print("No tasks in the list.")

if __name__ == "__main__":
    todo_list = TodoList()
    
    while True:
        print("\nTodo List Menu:")
        print("1. Add Task")
        print("2. Remove Task")
        print("3. View Tasks")
        print("4. Quit")
        choice = input("Enter your choice: ")

        if choice == "1":
            task = input("Enter the task: ")
            todo_list.add_task(task)
        elif choice == "2":
            task = input("Enter the task to remove: ")
            todo_list.remove_task(task)
        elif choice == "3":
            todo_list.view_tasks()
        elif choice == "4":
            print("Exiting the Todo List application. Goodbye!")
            break
            
TASK 2: CALCULATOR

def add(x, y):
    return x + y

def subtract(x, y):
    return x - y

def multiply(x, y):
    return x * y

def divide(x, y):
    if y == 0:
        return "Division by zero is not allowed."
    return x / y

while True:
    print("\nCalculator Menu:")
    print("1. Add")
    print("2. Subtract")
    print("3. Multiply")
    print("4. Divide")
    print("5. Quit")
    choice = input("Enter your choice: ")

    if choice == "5":
        print("Exiting the calculator. Goodbye!")
        break

    if choice not in ["1", "2", "3", "4"]:
        print("Invalid choice. Please enter a valid option.")
        continue

    num1 = float(input("Enter first number: "))
    num2 = float(input("Enter second number: "))

    if choice == "1":
        print("Result: ", add(num1, num2))
    elif choice == "2":
        print("Result: ", subtract(num1, num2))
    elif choice == "3":
        print("Result: ", multiply(num1, num2))
    elif choice == "4":
        print("Result: ", divide(num1, num2))

TASK 3: PASSWORD GENERATOR

import random
import string

def generate_password(length):
    characters = string.ascii_letters + string.digits + string.punctuation
    password = ''.join(random.choice(characters) for _ in range(length))
    return password

while True:
    length = int(input("Enter the desired password length: "))
    if length < 8:
        print("Password should be at least 8 characters long.")
    else:
        password = generate_password(length)
        print("Generated Password: " + password)
        break

        
TASK 4: ROCK-PAPER-SCISSORS GAME

import random

def get_user_choice():
    user_choice = input("Choose rock, paper, or scissors: ").lower()
    if user_choice in ["rock", "paper", "scissors"]:
        return user_choice
    else:
        print("Invalid choice. Please choose rock, paper, or scissors.")
        return get_user_choice()

def get_computer_choice():
    return random.choice(["rock", "paper", "scissors"])

def determine_winner(user_choice, computer_choice):
    if user_choice == computer_choice:
        return "It's a tie!"
    elif (user_choice == "rock" and computer_choice == "scissors") or \
         (user_choice == "scissors" and computer_choice == "paper") or \
         (user_choice == "paper" and computer_choice == "rock"):
        return "You win!"
    else:
        return "Computer wins!"

user_score = 0
computer_score = 0

while True:
    user_choice = get_user_choice()
    computer_choice = get_computer_choice()
    
    print(f"Your choice: {user_choice}")
    print(f"Computer's choice: {computer_choice}")
    
    result = determine_winner(user_choice, computer_choice)
    print(result)
    
    if result == "You win!":
        user_score += 1
    elif result == "Computer wins!":
        computer_score += 1
    
    print(f"Your Score: {user_score}")
    print(f"Computer's Score: {computer_score}")
    
    play_again = input("Do you want to play again? (yes/no): ").lower()
    if play_again != "yes":
        print("Game over. Thanks for playing!")
        break

TASK 5: CONTACT BOOK

class Contact:
    def __init__(self, name, phone, email, address):
        self.name = name
        self.phone = phone
        self.email = email
        self.address = address

class ContactBook:
    def __init__(self):
        self.contacts = []

    def add_contact(self, contact):
        self.contacts.append(contact)

    def view_contacts(self):
        for contact in self.contacts:
            print(f"Name: {contact.name}, Phone: {contact.phone}, Email: {contact.email}, Address: {contact.address}")

    def search_contact(self, search_term):
        matching_contacts = [contact for contact in self.contacts if search_term in contact.name or search_term in contact.phone]
        if matching_contacts:
            for contact in matching_contacts:
                print(f"Name: {contact.name}, Phone: {contact.phone}, Email: {contact.email}, Address: {contact.address}")
        else:
            print("No matching contacts found.")

    def update_contact(self, search_term, updated_contact):
        for contact in self.contacts:
            if search_term in contact.name or search_term in contact.phone:
                contact.name = updated_contact.name
                contact.phone = updated_contact.phone
                contact.email = updated_contact.email
                contact.address = updated_contact.address
                print("Contact updated successfully.")
                return

    def delete_contact(self, search_term):
        for contact in self.contacts:
            if search_term in contact.name or search_term in contact.phone:
                self.contacts.remove(contact)
                print("Contact deleted successfully.")
                return

if __name__ == "__main__":
    contact_book = ContactBook()
    
    while True:
        print("\nContact Book Menu:")
        print("1. Add Contact")
        print("2. View Contacts")
        print("3. Search Contact")
        print("4. Update Contact")
        print("5. Delete Contact")
        print("6. Quit")
        choice = input("Enter your choice: ")

        if choice == "6":
            print("Exiting the Contact Book application. Goodbye!")
            break

        if choice == "1":
            name = input("Enter Name: ")
            phone = input("Enter Phone: ")
            email = input("Enter Email: ")
            address = input("Enter Address: ")
            contact = Contact(name, phone, email, address)
            contact_book.add_contact(contact)
        elif choice == "2":
            contact_book.view_contacts()
        elif choice == "3":
            search_term = input("Enter a name or phone number to search: ")
            contact_book.search_contact(search_term)
        elif choice == "4":
            search_term = input("Enter a name or phone number to update: ")
            updated_name = input("Enter updated name: ")
            updated_phone = input("Enter updated phone: ")
            updated_email = input("Enter updated email: ")
            updated_address = input("Enter updated address: ")
            updated_contact = Contact(updated_name, updated_phone, updated_email, updated_address)
            contact_book.update_contact(search_term, updated_contact)
        elif choice == "5":
            search_term = input("Enter a name or phone number to delete: ")
            contact_book.delete_contact(search_term)






