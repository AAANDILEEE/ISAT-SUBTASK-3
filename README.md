# ISAT-SUBTASK-3
#include <iostream>
#include <string>
using namespace std;

// Maximum number of orders
const int MAX_ORDERS = 100;

// Parallel arrays
int orderID[MAX_ORDERS];
string customerName[MAX_ORDERS];
int number[MAX_ORDERS];
double totalAmount[MAX_ORDERS];

int orderCount = 0;  // track number of orders

// Function: Add new order
void addOrder() {
    if (orderCount < MAX_ORDERS) {
        int id, numb;
        string name;
        double price = 5.00; // Price per magwinya (example)

        cout << "Enter Order ID: ";
        cin >> id;
        cout << "Enter Customer Name: ";
        cin.ignore();
        getline(cin, name);
        cout << "Enter number of Magwinyas: ";
        cin >> numb;

        double total = numb * price;

        orderID[orderCount] = id;
        customerName[orderCount] = name;
        number[orderCount] = numb;
        totalAmount[orderCount] = total;

        orderCount++;
        cout << "Order added successfully!" << endl;
    } else {
        cout << "Order list is full!" << endl;
    }
}

// Function: Display all orders
void displayOrders() {
    if (orderCount == 0) {
        cout << "No orders available!" << endl;
        return;
    }
    cout << "\n===== All Orders =====" << endl;
    for (int i = 0; i < orderCount; i++) {
        cout << "Order ID: " << orderID[i]
             << ", Customer: " << customerName[i]
             << ", number: " << number[i]
             << ", Total: R" << totalAmount[i] << endl;
    }
}

// Function: Search by Order ID
void searchOrder() {
    int id;
    cout << "Enter Order ID to search: ";
    cin >> id;
    bool found = false;
    for (int i = 0; i < orderCount; i++) {
        if (orderID[i] == id) {
            cout << "Order Found -> "
                 << "Customer: " << customerName[i]
                 << ", number: " << number[i]
                 << ", Total: R" << totalAmount[i] << endl;
            found = true;
            break;
        }
    }
    if (!found) {
        cout << "Order ID not found!" << endl;
    }
}

// Function: Calculate total revenue
void calculateRevenue() {
    double revenue = 0;
    for (int i = 0; i < orderCount; i++) {
        revenue += totalAmount[i];
    }
    cout << "Total Revenue: R" << revenue << endl;
}

// Menu
void displayMenu() {
    cout << "\n===== Magwinya Magic Order System =====" << endl;
    cout << "1. Add Order" << endl;
    cout << "2. Display All Orders" << endl;
    cout << "3. Search Order by ID" << endl;
    cout << "4. Calculate Total Revenue" << endl;
    cout << "5. Exit" << endl;
    cout << "Enter your choice: ";
}

int main() {
    int choice;
    do {
        displayMenu();
        cin >> choice;

        switch(choice) {
            case 1: addOrder(); break;
            case 2: displayOrders(); break;
            case 3: searchOrder(); break;
            case 4: calculateRevenue(); break;
            case 5: cout << "Exiting program..." << endl; break;
            default: cout << "Invalid choice! Try again." << endl;
        }

    } while(choice != 5);
    return 0;
}
