Question:
You are tasked with developing a vending machine application. The vending machine should allow customers to select from a variety of soft drinks and make payments. The program should display the available drinks with their prices and quantities, accept the customer's choice and money, dispense the selected drink, calculate and return the change, and update the quantity of the selected drink. Write a C++ program that implements this vending machine functionality.



#include<iostream>
#include <stdlib.h>
#include <string.h>
#include <iomanip>
using namespace std;

struct softdrink {
    char name[20];
    float price;
    unsigned quantity;
};

int main() {
    softdrink drink[5];

    strcpy(drink[0].name,"Cola"); drink[0].price=0.75; drink[0].quantity=20;
    strcpy(drink[1].name,"Root Beer"); drink[1].price=0.75; drink[1].quantity=20;
    strcpy(drink[2].name,"Lemon Lime"); drink[2].price=0.75; drink[2].quantity=20;
    strcpy(drink[3].name,"Grape Soda"); drink[3].price=0.80; drink[3].quantity=20;
    strcpy(drink[4].name,"Cream Soda"); drink[4].price=0.80; drink[4].quantity=20;

    std::cout << std::fixed;
    std::cout << std::setprecision(4);

    int choice = 1;

    while (choice != 6) {
        cout << "\n 1) " << drink[0].name << "\t\t" << drink[0].price << "\t(" << drink[0].quantity << ") remaining";
        cout << "\n 2) " << drink[1].name << "\t\t" << drink[1].price << "\t(" << drink[1].quantity << ") remaining";
        cout << "\n 3) " << drink[2].name << "\t\t" << drink[2].price << "\t(" << drink[2].quantity << ") remaining";
        cout << "\n 4) " << drink[3].name << "\t\t" << drink[3].price << "\t(" << drink[3].quantity << ") remaining";
        cout << "\n 5) " << drink[4].name << "\t\t" << drink[4].price << "\t(" << drink[4].quantity << ") remaining";
        cout << "\n 6) Leave the drink machine \n\n";
        cout << "\n Choose one: ";
        cin >> choice;

        if (choice >= 1 && choice <= 5) {
            if (drink[choice-1].quantity == 0) {
                cout << "\n No more " << drink[choice-1].name << " Available ..";
                getchar(); getchar();
                continue;
            }
        }

        if (choice == 6)
            cout << "Thank you for using it!";
        else if (choice <= 5) {
            float money;
            cout << "\n Enter any amount of money: ";
            cin >> money;

            float price;
            if (choice >= 1 && choice <= 3) {
                price = 0.75;
                if (money < price) {
                    cout << "\n Enter sufficient amount ";
                    getchar(); getchar();
                    continue;
                }
            }
            else if (choice == 4 || choice == 5) {
                price = 0.80;
                if (money < price) {
                    cout << "\n Enter sufficient amount ";
                    getchar(); getchar();
                    continue;
                }
            }
            cout << "\n Thum, thum, thum, splat !";
            cout << "\n Enjoy your beverage ";
            cout << "\n\n Change calculated: " << money - price;
            cout << "\n Your change, " << money - price << " just dropped into the Change Dispenser.";
            drink[choice-1].quantity = drink[choice-1].quantity - 1;

            cout << "\n There are " << drink[choice-1].quantity << " drinks of that type left";

            getchar();
            getchar();
        }
        else {
            cout << "\n Warning: Invalid Choice ";
        }
    }

    return 0;
}

                    
                    
                                                                    Explanation:
The above code is an implementation of a vending machine application in C++. It allows customers to select from a menu of soft drinks, make payments, and receive the selected drink along with any change. Here's how it works:

The code defines a structure softdrink to store information about each drink, including its name, price, and quantity.
An array of softdrink objects named drink is created to represent the available drinks in the vending machine.
The menu of available drinks is displayed to the user, along with their prices and remaining quantities.
The user is prompted to choose a drink by entering a number corresponding to the drink's position in the menu.
If the chosen drink is out of stock (quantity is zero), a message is displayed, and the user is prompted again for another choice.
If the user chooses to leave the machine (option 6), a farewell message is displayed, and the program terminates.
If the user chooses a valid drink (options 1 to 5), they are prompted to enter the amount of money they want to insert.
The program checks if the inserted amount is sufficient for the chosen drink. If not, an error message is displayed, and the user is prompted again for the amount.
If the inserted amount is sufficient, the program displays a message indicating the successful dispensing of the drink and calculates the change by subtracting the drink's price from the inserted amount.
The change amount is displayed, and the quantity of the chosen drink is reduced by 1.
The program then displays the remaining quantity of the chosen drink.
The user is prompted to press any key to continue.
The program returns to the main menu to allow the user to make another choice.
This process continues until the user chooses to leave the vending machine (option 6).

Note: The code uses the C++ strcpy function to copy the drink names into the name fields of the softdrink structure. However, it is recommended to use std::string instead of character arrays for string handling in modern C++.
