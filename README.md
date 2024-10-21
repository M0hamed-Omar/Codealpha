# To Do List Application

This is a simple command-line To Do List application built using C++. It allows users to manage their tasks by adding, completing, and deleting tasks from their list.

## Features

- Add tasks to the list.
- Complete tasks (remove them from the list).
- Delete specific tasks from the list.
- Display the current tasks.

## How to Use

1. Compile the program using a C++ compiler.
2. Run the executable file.
3. Follow the prompts to manage your tasks.

## Code Overview

The main functions in the application include:

- **display()**: Displays the current tasks.
- **complete()**: Marks a task as completed and removes it from the list.
- **main()**: Contains the main loop for user interaction.

## Requirements

- C++ compiler (supports C++11 or later).
- Windows environment (for Windows-specific headers).

## C++ Code Example

```cpp
#include<iostream>
#include<Windows.h>
#include<string>
using namespace std;

void display(string operations[], int task_count)
{
    cout << "======================\n";
    cout << "         your  tasks  :                      \n";
    for (int i = 0; i < task_count; i++)
        cout << i + 1 << "-" << operations[i] << "\n";
    cout << "======================\n";
}

void complete(string operations[], int &task_count)
{
    int com;
    cout << "Enter the number of completed task:\n";
    cin >> com;
    if (com > 0 && com <= task_count)
    {
        for (int i = com - 1; i < task_count - 1; i++)
        {
            operations[i] = operations[i + 1];
        }
        operations[task_count - 1] = "";
        task_count--;
    }
}

int main() {
    system("color 1");
    int del;
    string operations[10] = { "" };
    int task_count = 0;
    int operation = 0;
    while (operation != 4)
    {
        cout << "        To Do List   \n";
        display(operations, task_count);
        cout << "1-Add Task\n";
        cout << "2-Complete Task\n";
        cout << "3-Delete Task\n";
        cout << "4-Close the program \n";
        cin >> operation;
        cin.ignore();
        switch (operation)
        {
        case 1:
            if (task_count > 9)
            {
                cout << "your list is full\n";
                break;
            }
            else {
                cout << "Enter new task:\n";
                getline(cin ,operations[task_count]);
                task_count++;
                break;
            }
        case 2:
            complete(operations, task_count);
            break;
        case 3:
            cout << "Enter number of task you would delete:\n";
            cin >> del;
            if (del > 0 && del <= task_count)
            {
                for (int i = del - 1; i < task_count - 1; i++)
                {
                    operations[i] = operations[i + 1];
                }
                operations[task_count - 1] = "";
                task_count--;
            }
            break;
        case 4:
            cout << "program closed\n";
            break;
        default:
            cout << "invalid\n";
            break;
        }
    }
    return 0;
}
