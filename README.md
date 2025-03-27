# STUDENT-INFORMATION-SYSTEM.
/*                      Project 2- STUDENT INFORMATION SYSTEM.
It is a simple c++ project for Student Information System.It gives a simple example of a complete system with the
functionality of add record, search record, Update record and delete record using linked list. 
If students understand basic CRUD (Create, Read, Update and Delete) functionality it would be easy for them to create any
Management System using this functionality. The Project has 4 major function in menu:
1. Add New record
2. Search a record
3. Modify a record
4. Delete a record
Details to help implement:
The menu is handled by if else statement. While adding a new record, if any node already exist then new node is connected
with it otherwise a new node is created. While searching a node, a pointer searches all the pointers of linked lists to
match the required data from start to end. While Modification the data part of the linked list is overwritten with new data
& in case of Deletion, the pointers before & after of the node which we need to delete are connected with each other */
#include <iostream>
#include <string>
using namespace std;
struct Student { 
    int id;
    string name;
    Student* next; };
Student* head = nullptr;
void addStudent() {
    int id;
    string name;
    cout << "Enter Student ID (Integer): ";
    cin >> id;
    cin.ignore(); // Ignores the next character in the input buffer (typically the newline character).
    cout << "Enter Student Name: ";
    getline(cin, name);
    Student* newStudent = new Student{id, name, nullptr};
    if (!head) {
        head = newStudent; } 
    else {
        Student* temp = head;
        while (temp->next) {
            temp = temp->next; }
        temp->next = newStudent; }
    cout << "Student added successfully!" << endl; }
void searchStudent() {
    int id;
    cout << "Enter Student ID to search: ";
    cin >> id;
    Student* temp = head;
    while (temp) {
        if (temp->id == id) {
        cout << "Student Found: " << temp->name << endl;
            return;    }
        temp = temp->next;    }
    cout << "Student not found!" << endl;   }
void modifyStudent() {
    int id;
    cout << "Enter Student ID to modify: ";
    cin >> id;
    cin.ignore();
    Student* temp = head;
    while (temp) {
        if (temp->id == id) {
            cout << "Enter new name: ";
            getline(cin, temp->name);
            cout << "Student record updated successfully!" << endl;
            return;    }
        temp = temp->next;    }
    cout << "Student not found!" << endl; }
void deleteStudent() {
    int id;
    cout << "Enter Student ID to delete: ";
    cin >> id;
    if (head && head->id == id) {
        Student* temp = head;
        head = head->next;
        delete temp;
        cout << "Student deleted successfully!" << endl;
        return;    }
    Student* current = head;
    Student* previous = nullptr;
    while (current && current->id != id) {
        previous = current;
        current = current->next;    }
    if (current) {
        previous->next = current->next;
        delete current;
        cout << "Student deleted successfully!" << endl;
    } else {
        cout << "Student not found!" << endl;   }}
int main() {
    int choice;
    while (true) {
    cout << "1. Add New Record\n2. Search a Record\n3. Modify a Record\n4. Delete a Record\n5. Exit\n";
    cout << "Enter your choice: ";
    cin >> choice;
    switch (choice) {
        case 1: addStudent(); break;
        case 2: searchStudent(); break;
        case 3: modifyStudent(); break;
        case 4: deleteStudent(); break;
        case 5: return 0;
        default: cout << "Invalid choice!" << endl; }}}


































