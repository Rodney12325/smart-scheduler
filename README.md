exams = []

def display_menu():
    print("\n--- Smart Scheduler Menu ---")
    print("1. Add a new exam")
    print("2. View all exams")
    print("3. Edit an exam entry")
    print("4. Delete an exam entry")
    print("5. Exit")
    print("-----------------------------")

def add_exam():
    exam_name = input("Enter exam name: ")
    exam_date = input("Enter exam date (YYYY-MM-DD): ")
    exam_time = input("Enter exam time (HH:MM): ")
    exam_room = input("Enter assigned room: ")
    
    exam = {
        'name': exam_name,
        'date': exam_date,
        'time': exam_time,
        'room': exam_room
    }
    
    exams.append(exam)
    print("Exam added successfully!")

def view_exams():
    if not exams:
        print("No exams scheduled.")
        return
    
    print("\n--- Scheduled Exams ---")
    for index, exam in enumerate(exams):
        print(f"{index + 1}. Name: {exam['name']}, Date: {exam['date']}, Time: {exam['time']}, Room: {exam['room']}")
    print("-----------------------")

def edit_exam():
    view_exams()
    try:
        exam_index = int(input("Enter the exam number to edit: ")) - 1
        if 0 <= exam_index < len(exams):
            exam_name = input("Enter new exam name (leave blank to keep current): ")
            exam_date = input("Enter new exam date (leave blank to keep current): ")
            exam_time = input("Enter new exam time (leave blank to keep current): ")
            exam_room = input("Enter new assigned room (leave blank to keep current): ")

            if exam_name:
                exams[exam_index]['name'] = exam_name
            if exam_date:
                exams[exam_index]['date'] = exam_date
            if exam_time:
                exams[exam_index]['time'] = exam_time
            if exam_room:
                exams[exam_index]['room'] = exam_room
            
            print("Exam updated successfully!")
        else:
            print("Invalid exam number.")
    except ValueError:
        print("Please enter a valid number.")

def delete_exam():
    view_exams()
    try:
        exam_index = int(input("Enter the exam number to delete: ")) - 1
        if 0 <= exam_index < len(exams):
            exams.pop(exam_index)
            print("Exam deleted successfully!")
        else:
            print("Invalid exam number.")
    except ValueError:
        print("Please enter a valid number.")

def main():
    while True:
        display_menu()
        choice = input("Select an option: ")
        
        if choice == '1':
            add_exam()
        elif choice == '2':
            view_exams()
        elif choice == '3':
            edit_exam()
        elif choice == '4':
            delete_exam()
        elif choice == '5':
            print("Exiting the Smart Scheduler. Goodbye!")
            break
        else:
            print("Invalid option. Please try again.")

if __name__ == "__main__":
    main()
