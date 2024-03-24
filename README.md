# Task-4-C-

#include <iostream>
#include <vector>
using namespace std;

class ToDoList {
private:
    vector<struct Task> tasks;

public:
    struct Task {
        string task;
        bool completed;
    };

    void add_task(string task) {
        tasks.push_back({task, false});
    }

    void view_tasks() {
        if (tasks.empty()) {
            cout << "No tasks added." << endl;
        } else {
            cout << "Tasks:" << endl;
            for (int i = 0; i < tasks.size(); i++) {
                string status = tasks[i].completed ? "Completed" : "Pending";
                cout << i + 1 << ". " << tasks[i].task << " - " << status << endl;
            }
        }
    }

    void mark_completed(int task_index) {
        if (task_index >= 1 && task_index <= tasks.size()) {
            tasks[task_index - 1].completed = true;
            cout << "Task marked as completed." << endl;
        } else {
            cout << "Invalid task index." << endl;
        }
    }

    void remove_task(int task_index) {
        if (task_index >= 1 && task_index <= tasks.size()) {
            tasks.erase(tasks.begin() + task_index - 1);
            cout << "Task removed." << endl;
        } else {
            cout << "Invalid task index." << endl;
        }
    }
};

int main() {
    ToDoList todo_list;
    while (true) {
        cout << endl;
        cout << "1. Add Task" << endl;
        cout << "2. View Tasks" << endl;
        cout << "3. Mark Task as Completed" << endl;
        cout << "4. Remove Task" << endl;
        cout << "5. Exit" << endl;
        cout << "Enter your choice (1-5): ";
        int choice;
        cin >> choice;
        cin.ignore();

        if (choice == 1) {
            string task;
            cout << "Enter task to add: ";
            getline(cin, task);
            todo_list.add_task(task);
        } else if (choice == 2) {
            todo_list.view_tasks();
        } else if (choice == 3) {
            int task_index;
            cout << "Enter task index to mark as completed: ";
            cin >> task_index;
            cin.ignore();
            todo_list.mark_completed(task_index);
        } else if (choice == 4) {
            int task_index;
            cout << "Enter task index to remove: ";
            cin >> task_index;
            cin.ignore();
            todo_list.remove_task(task_index);
        } else if (choice == 5) {
            cout << "Exiting..." << endl;
            break;
        } else {
            cout << "Invalid choice. Please try again." << endl;
        }
    }
    return 0;
}

