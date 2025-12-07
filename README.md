# Student Record Management System (SRMS)

A console-based Student Record Management System written in C++ that provides complete CRUD (Create, Read, Update, Delete) operations with file-based persistence. This project demonstrates fundamental programming concepts including file I/O, data structures, input validation, and interactive console UI design.

## Features

- ✅ **Add students** with user-provided alphanumeric IDs (must contain both letters and digits)
- ✅ **Display all students** in a formatted table view
- ✅ **Search students** by ID with detailed record display
- ✅ **Update student records** (name, age, course, GPA)
- ✅ **Delete student records** with confirmation
- ✅ **Persistent storage** using text file (`students.txt`)
- ✅ **Input validation** for IDs, GPA, and age
- ✅ **Unique ID enforcement** prevents duplicate entries
- ✅ **Interactive menu system** with continuous operation

## Project Structure

```
SRMS/
├── main.cpp                              # Entry point and menu loop
├── Student.h                             # Student class declaration
├── Student.cpp                           # Student class implementation
├── StudentManagementSystem.h            # System class declaration
├── StudentManagementSystem.cpp          # Core CRUD logic and file I/O
├── students.txt                          # Auto-generated data file
├── output/                               # Optional folder for sample outputs
└── README.md                             # This file
```

### File Descriptions

**`main.cpp`**
- Application entry point
- Interactive menu loop
- User input handling for menu choices
- Continuous operation with "show menu again" prompts

**`Student.h` / `Student.cpp`**
- `Student` class definition and implementation
- Properties: ID (string), Name, Age, Course, GPA
- Getter and setter methods
- Display formatting methods

**`StudentManagementSystem.h` / `StudentManagementSystem.cpp`**
- Core management logic:
  - `addStudent()` - Add new student with validation
  - `displayAllStudents()` - Show formatted table
  - `searchStudent()` - Find by ID
  - `updateStudent()` - Modify existing records
  - `deleteStudent()` - Remove records
  - `saveToFile()` - Persist data
  - `loadFromFile()` - Restore data on startup
- Input validation functions
- Vector-based student storage

**`students.txt`**
- Auto-created at runtime
- Stores all student records
- Simple text format (see File Format section)

## Prerequisites

- **Operating System**: Windows, Linux, or macOS
- **C++ Compiler** with C++11 support:
  - Windows: MinGW, MSYS2, or Visual Studio
  - Linux: g++ (GNU Compiler Collection)
  - macOS: Clang (via Xcode Command Line Tools)

## Build Instructions

### Windows (PowerShell or Command Prompt)

Using **MinGW** or **MSYS2**:

```powershell
g++ -std=c++11 main.cpp StudentManagementSystem.cpp Student.cpp -o srms.exe
```

Using **Visual Studio Developer Command Prompt**:

```cmd
cl /EHsc /std:c++11 main.cpp StudentManagementSystem.cpp Student.cpp /Fe:srms.exe
```

### Linux / macOS

```bash
g++ -std=c++11 main.cpp StudentManagementSystem.cpp Student.cpp -o srms
```

### CMake (Optional - Cross-Platform)

Create `CMakeLists.txt`:

```cmake
cmake_minimum_required(VERSION 3.10)
project(SRMS)

set(CMAKE_CXX_STANDARD 11)

add_executable(srms 
    main.cpp 
    Student.cpp 
    StudentManagementSystem.cpp
)
```

Build:
```bash
mkdir build && cd build
cmake ..
cmake --build .
```

## Running the Application

### Windows
```powershell
.\srms.exe
```
or double-click `srms.exe` in File Explorer

### Linux / macOS
```bash
./srms
```

## Usage Guide

### Main Menu

```
========================================
  Student Record Management System
========================================
1. Add Student
2. Display All Students
3. Search Student
4. Update Student
5. Delete Student
6. Exit
========================================
Enter your choice: _
```

### Adding a Student

1. Select option **1** from the main menu
2. Enter a **Student ID**:
   - Must contain **only letters and digits** (no spaces or special characters)
   - Must include **at least one letter** AND **at least one digit**
   - Must be **unique** (not already in use)
   - Examples: `S001`, `STUD123`, `2024CS001`, `JohnD42`
3. Enter **Name** (string, can contain spaces)
4. Enter **Age** (integer, validated range)
5. Enter **Course** (string, e.g., "Computer Science")
6. Enter **GPA** (decimal, typically 0.0 - 4.0)

**Example:**
```
Enter Student ID: CS2024A
Enter Name: Terish
Enter Age: 18
Enter Course: Computer Science
Enter GPA: 9.75

Student added successfully!
```

### Displaying All Students

Select option **2** to view all records in a formatted table:

```
========================================
           All Students
========================================
ID        | Name           | Age | Course              | GPA
----------|----------------|-----|---------------------|------
CS2024A   | Terish         | 18  | Computer Science    | 3.75
ENG123B   | Jane Smith     | 21  | Engineering         | 3.90
========================================
Total Students: 2
========================================
```

### Searching for a Student

1. Select option **3**
2. Enter the **Student ID** to search
3. View detailed information if found

**Example:**
```
Enter Student ID to search: CS2024A

Student Found:
--------------
ID: CS2024A
Name: Terish
Age: 18
Course: Computer Science
GPA: 9.75
```

### Updating a Student

1. Select option **4**
2. Enter the **Student ID** to update
3. Choose what to update:
   - Name
   - Age
   - Course
   - GPA
4. Enter new value

**Example:**
```
Enter Student ID to update: CS2024A
Current GPA: 9.75
Enter new GPA: 9.85

Student updated successfully!
```

### Deleting a Student

1. Select option **5**
2. Enter the **Student ID** to delete
3. Confirm deletion

**Example:**
```
Enter Student ID to delete: CS2024A
Are you sure you want to delete this student? (y/n): y

Student deleted successfully!
```

### Exiting

Select option **6** to exit the program. All changes are automatically saved to `students.txt`.

## File Format

### students.txt Structure

The data file uses a simple line-based format:

```
<nextId>           # Line 1: Legacy ID counter (kept for compatibility)
<ID>               # Line 2: First student ID
<Name>             # Line 3: First student name
<Age>              # Line 4: First student age
<Course>           # Line 5: First student course
<GPA>              # Line 6: First student GPA
<ID>               # Line 7: Second student ID
<Name>             # Line 8: Second student name
...
```

**Example `students.txt`:**
```
1000
CS2024A
Terish
20
Computer Science
9.75
ENG123B
Maneesh
21
Engineering
9.90
```

**Note**: Each student record occupies exactly 5 lines after the first line.

## Input Validation Rules

### Student ID
- ✅ Contains only alphanumeric characters (a-z, A-Z, 0-9)
- ✅ Must include at least one letter
- ✅ Must include at least one digit
- ✅ Must be unique across all students
- ❌ No spaces, hyphens, or special characters

**Valid Examples**: `S001`, `STUDENT123`, `2024CS001`, `JD42`, `A1B2C3`  
**Invalid Examples**: `123` (no letters), `ABC` (no digits), `S-001` (special char), `S 001` (space)

### Age
- Must be a positive integer
- Typical range: 1-150 (adjust in code as needed)

### GPA
- Must be a decimal number
- Typical range: 0.0-10.0 (US system)
- Can be adjusted for other grading systems (0-10, 0-100, etc.)

### Name and Course
- Any non-empty string
- Can contain spaces and special characters
- Maximum length limited by system

## Common Issues & Solutions

### Build Errors

**Error: `'to_string' is not a member of 'std'`**
- Solution: Ensure you're using `-std=c++11` or higher

**Error: `undefined reference to Student::Student()`**
- Solution: Make sure all `.cpp` files are included in the compilation command

**Error: Permission denied**
- Solution: Ensure you have write permissions in the directory

### Runtime Issues

**Problem: students.txt not found**
- Solution: The file is auto-created on first run. If issues persist, create an empty file manually with just `0` on the first line.

**Problem: Data not persisting**
- Solution: Check file permissions and ensure the program completes normally (doesn't crash)

**Problem: Invalid ID format errors**
- Solution: Remember IDs must have BOTH letters AND digits. Use format like `S001`, not `001` or `STUD`.

**Problem: Cannot add student - ID already exists**
- Solution: Each ID must be unique. Search for the existing student or choose a different ID.

### Display Issues

**Problem: Table formatting looks broken**
- Solution: Use a monospace font in your terminal
- On Windows, ensure console is wide enough (resize window)

**Problem: Special characters display incorrectly**
- Solution: Use ASCII characters only, or configure console for UTF-8 encoding

## Configuration Options

### Changing Validation Ranges

Edit `StudentManagementSystem.cpp`:

```cpp
// Age validation
if (age < 1 || age > 150) {
    cout << "Invalid age. Please enter between 1 and 150." << endl;
    return;
}

// GPA validation
if (gpa < 0.0 || gpa > 10.0) {
    cout << "Invalid GPA. Please enter between 0.0 and 4.0." << endl;
    return;
}
```

### Changing File Name

In `StudentManagementSystem.h`, modify:

```cpp
const string FILENAME = "students.txt";  // Change to your preferred name
```

### Adding New Fields

1. Add property to `Student` class in `Student.h`
2. Add getter/setter methods
3. Update file I/O in `StudentManagementSystem.cpp`
4. Update display and input functions

## Learning Objectives

This project demonstrates:

- **Object-Oriented Programming**: Classes, encapsulation, separation of concerns
- **File I/O**: Reading and writing structured data to files
- **Data Structures**: Using `std::vector` for dynamic storage
- **Input Validation**: Ensuring data integrity
- **User Interface**: Console-based menu systems
- **CRUD Operations**: Complete data management lifecycle
- **State Persistence**: Maintaining data between program runs

## Future Enhancement Ideas

### Beginner Level
- [ ] Add student ID auto-generation option
- [ ] Case-insensitive search
- [ ] Sort students by name, GPA, or age
- [ ] Export data to CSV format
- [ ] Import data from CSV

### Intermediate Level
- [ ] Add search by name or course
- [ ] Implement filters (e.g., show students with GPA > 3.5)
- [ ] Add pagination for large datasets
- [ ] Implement undo/redo functionality
- [ ] Add data backup and restore
- [ ] Generate student reports

### Advanced Level
- [ ] Migrate to SQLite database
- [ ] Create GUI using Qt or wxWidgets
- [ ] Add multi-user support with authentication
- [ ] Implement data encryption
- [ ] Create RESTful API for web integration
- [ ] Add statistical analysis and charts
- [ ] Implement course enrollment system
- [ ] Add attendance tracking
- [ ] Generate transcripts and grade reports

## Testing Checklist

- [ ] Add student with valid ID
- [ ] Attempt to add student with duplicate ID
- [ ] Attempt to add student with invalid ID (no letters or no digits)
- [ ] Display all students when empty
- [ ] Display all students with multiple records
- [ ] Search for existing student
- [ ] Search for non-existent student
- [ ] Update each field of a student
- [ ] Delete student
- [ ] Exit and restart - verify data persists
- [ ] Test GPA and age boundary values
- [ ] Test with special characters in names

## Contributing

This is an educational project. Contributions are welcome:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/NewFeature`)
3. Commit your changes (`git commit -m 'Add NewFeature'`)
4. Push to the branch (`git push origin feature/NewFeature`)
5. Open a Pull Request

## Code Style Guidelines

- Use camelCase for variable and function names
- Use PascalCase for class names
- Add comments for complex logic
- Keep functions focused and single-purpose
- Use meaningful variable names

## License

This project is provided as-is for educational purposes. Feel free to modify and distribute. Add a `LICENSE` file if you want to specify formal terms.

## Resources

- [C++ File I/O Tutorial](https://www.cplusplus.com/doc/tutorial/files/)
- [C++ Vectors](https://www.cplusplus.com/reference/vector/vector/)
- [C++ Classes and Objects](https://www.cplusplus.com/doc/tutorial/classes/)
- [Input Validation in C++](https://www.learncpp.com/cpp-tutorial/stdcin-and-handling-invalid-input/)

## Support

**Need help?** 
- Check the Common Issues section above
- Review the code comments in source files
- Open an issue describing your problem

**Want to extend this project?**
Tell me what feature you'd like to add next, and I can provide guidance on implementation!

---

**Version**: 1.0  
**Language**: C++11  
**Platform**: Cross-platform (Windows, Linux, macOS)  
**Type**: Educational Console Application
