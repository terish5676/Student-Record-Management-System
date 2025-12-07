# Student Record Management System (SRMS)

Simple console-based Student Record Management System written in C++.
This project provides basic CRUD features with file-based persistence and
allows alphanumeric student IDs (user-provided). It is intended as a small
desktop/school project to demonstrate file I/O, basic data structures, and
console UI in C++.

**Project layout**

- `main.cpp` - entry point and interactive menu loop.
- `Student.h` / `Student.cpp` - `Student` class (stores ID, name, age, course, GPA).
- `StudentManagementSystem.h` / `StudentManagementSystem.cpp` - core logic:
	add/search/update/delete students, file save/load, input validation.
- `students.txt` - (created at runtime) stores persistent student records.
- `output/` - optional folder for any sample outputs (not required).

Features
- Add student with user-provided alphanumeric ID (must contain letters and digits and be unique).
- Display all students in a nicely formatted table.
- Search, update, and delete student records by ID.
- Data persists between runs via a simple text file (`students.txt`).

Build (Windows — PowerShell example)

Make sure you have a C++ compiler installed (e.g., `g++` from MinGW or MSYS2).
From the project folder run:

```powershell
g++ -std=c++11 main.cpp StudentManagementSystem.cpp Student.cpp -o srms.exe
```

Run

```powershell
./srms.exe
```

or double-click `srms.exe` from File Explorer.

Usage notes
- Menu-driven console interface. After performing any action, the program
	prompts whether to show the menu again.
- When adding a student you are asked to enter an ID. The ID must:
	- contain only letters and digits (no spaces or symbols)
	- include at least one letter and at least one digit
	- be unique among existing student records
- GPA and age have basic validation ranges. Follow prompts for acceptable input.
- The student data is written to `students.txt` automatically when records
	are added, updated, or deleted.

File format (`students.txt`)
- The program currently stores data in a simple human-readable format:
	1st line: `nextId` (kept for backward compatibility)
	then for each student:
	- ID (string)
	- Name
	- Age
	- Course
	- GPA

Notes and future ideas
- Consider migrating to CSV or JSON for easier interoperability.
- Add unit tests and input sanitization improvements.
- Add sorting, filtering, or an interactive TUI (ncurses) / GUI.

Contact
If you want help extending this project, tell me what feature you'd like next.
