# Dictionary to store student contact information
students = {}

while True:
    print("\nStudent Contact Database")
    print("1. Add new entry")
    print("2. Update contact information")
    print("3. Remove entry")
    print("4. Search by ID")
    print("5. Search by Name")
    print("6. Display all students")
    print("7. Exit")

    choice = input("Enter your choice: ")

    if choice == "1":  # Add new entry
        student_id = input("Enter Student ID: ")
        if student_id in students:
            print("Student ID already exists!")
        else:
            name = input("Enter Name: ")
            phone = input("Enter Phone Number: ")
            email = input("Enter Email: ")
            students[student_id] = (name, phone, email)
            print("Student added successfully!")

    elif choice == "2":  # Update contact information
        student_id = input("Enter Student ID to update: ")
        if student_id in students:
            name = input("Enter new Name (leave blank to keep current): ") or students[student_id][0]
            phone = input("Enter new Phone Number (leave blank to keep current): ") or students[student_id][1]
            email = input("Enter new Email (leave blank to keep current): ") or students[student_id][2]
            students[student_id] = (name, phone, email)
            print("Student information updated successfully!")
        else:
            print("Student ID not found!")

    elif choice == "3":  # Remove entry
        student_id = input("Enter Student ID to remove: ")
        if student_id in students:
            del students[student_id]
            print("Student removed successfully!")
        else:
            print("Student ID not found!")

    elif choice == "4":  # Search by ID
        student_id = input("Enter Student ID to search: ")
        if student_id in students:
            print("Student Found:", students[student_id])
        else:
            print("Student ID not found!")

    elif choice == "5":  # Search by Name
        name = input("Enter Name to search: ")
        found = False
        for sid, details in students.items():
            if details[0].lower() == name.lower():
                print(f"ID: {sid}, Name: {details[0]}, Phone: {details[1]}, Email: {details[2]}")
                found = True
        if not found:
            print("No student found with that name!")

    elif choice == "6":  # Display all students
        if students:
            for sid, details in students.items():
                print(f"ID: {sid}, Name: {details[0]}, Phone: {details[1]}, Email: {details[2]}")
        else:
            print("No students in the database!")

    elif choice == "7":  # Exit
        print("Exiting program.")
        break

    else:
        print("Invalid choice! Please enter a number between 1 and 7.")
