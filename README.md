# Attendance-manager-
A simple Python Attendance Manager that allows users to add students, mark them as present or absent, and calculate their attendance percentage.
print("===== ATTENDANCE MANAGER =====")

students = []

while True:
    print("\n1. Add Student")
    print("2. Mark Attendance")
    print("3. View Attendance")
    print("4. Exit")

    choice = input("Enter your choice: ")

    if choice == "1":
        name = input("Enter student name: ")

        student = {
            "name": name,
            "present": 0,
            "total": 0
        }

        students.append(student)

        print("Student added successfully!")

    elif choice == "2":
        if len(students) == 0:
            print("No students found.")
        else:
            for student in students:
                print("\nStudent:", student["name"])

                status = input(
                    "Enter P for Present or A for Absent: "
                ).upper()

                if status == "P":
                    student["present"] += 1
                    student["total"] += 1
                    print("Marked Present.")

                elif status == "A":
                    student["total"] += 1
                    print("Marked Absent.")

                else:
                    print("Invalid attendance status.")

    elif choice == "3":
        print("\n===== ATTENDANCE REPORT =====")

        if len(students) == 0:
            print("No students found.")
        else:
            for student in students:
                if student["total"] > 0:
                    percentage = (
                        student["present"] /
                        student["total"]
                    ) * 100
                else:
                    percentage = 0

                print("\nName:", student["name"])
                print("Present:", student["present"])
                print("Total Classes:", student["total"])
                print("Attendance:", round(percentage, 2), "%")

    elif choice == "4":
        print("Thank you!")
        break

    else:
        print("Invalid choice!")
