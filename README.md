# Student Management System
students = []

def add_student():
    print("\n--- Add New Student ---")
    name = input("Enter name: ")
    roll_number = input("Enter roll number: ")
    age = int(input("Enter age: "))
    student_class = input("Enter class: ")

    student = {
        "name": name,
        "roll_number": roll_number,
        "age": age,
        "class": student_class
    }
    students.append(student)
    print(f"\nStudent {name} added successfully!")

def view_students():
    print("\n--- View All Students ---")
    if students:
        print(f"{'Name':<20} {'Roll No.':<10} {'Age':<5} {'Class':<10}")
        print("-" * 50)
        for student in students:
            print(f"{student['name']:<20} {student['roll_number']:<10} {student['age']:<5} {student['class']:<10}")
    else:
        print("No students found.")

def update_student():
    print("\n--- Update Student Information ---")
    roll_number = input("Enter roll number of student to update: ")
    
 
    student = next((s for s in students if s['roll_number'] == roll_number), None)

    if student:
        print(f"Current details: {student}")
        name = input(f"Enter new name (current: {student['name']}): ") or student['name']
        age = input(f"Enter new age (current: {student['age']}): ") or student['age']
        student_class = input(f"Enter new class (current: {student['class']}): ") or student['class']

        # Update the student details
        student['name'] = name
        student['age'] = int(age)
        student['class'] = student_class

        print(f"\nStudent {roll_number} updated successfully!")
    else:
        print(f"Student with roll number {roll_number} not found.")

def delete_student():
    print("\n--- Delete Student ---")
    roll_number = input("Enter roll number of student to delete: ")

    student = next((s for s in students if s['roll_number'] == roll_number), None)

    if student:
        students.remove(student)
        print(f"\nStudent {roll_number} deleted successfully!")
    else:
        print(f"Student with roll number {roll_number} not found.")

def main():
    while True:
        print("\n--- Student Management System ---")
        print("1. Add Student")
        print("2. View Students")
        print("3. Update Student")
        print("4. Delete Student")
        print("5. Exit")

        choice = input("\nEnter your choice (1-5): ")

        if choice == '1':
            add_student()
        elif choice == '2':
            view_students()
        elif choice == '3':
            update_student()
        elif choice == '4':
            delete_student()
        elif choice == '5':
            print("\nExiting the system...")
            break
        else:
            print("Invalid choice, please try again.")

if __name__ == "__main__":
    main()
11
