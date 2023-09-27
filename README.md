#include <conio.h>
#include <iostream>
#include <string>
using namespace std;

class atm {
private:
    long int Account_number;
    string Name;
    int Pin;
    double Balance;
    string Mobile_No;

public:
    void setData(long int Account_number_a, string Name_a, int Pin_a, double Balance_a, string Mobile_No_a) {
        Account_number = Account_number_a;
        Name = Name_a;
        Pin = Pin_a;
        Balance = Balance_a;
        Mobile_No = Mobile_No_a;
    }

    long int getAccountNumber() {
        return Account_number;
    }

    string getName() {
        return Name;
    }

    int getPin() {
        return Pin;
    }

    double getBalance() {
        return Balance;
    }

    string getMobile_No() {
        return Mobile_No;
    }

    void setMobile(string mob_prev, string mob_new) {
        if (mob_prev == Mobile_No) {
            Mobile_No = mob_new;
            cout << endl << "Successfully updated mobile No: ";
            _getch();
        }
        else {
            cout << endl << "Incorrect!! Old Mobile No. ";
            _getch();
        }
    }

    void cashWithDraw(int amount_a) {
        if (amount_a > 0 && amount_a <= Balance) {
            Balance -= amount_a;
            cout << endl << "Please Collect Your Cash ";
            cout << endl << "Available Balance: " << Balance;
            _getch();
        }
        else {
            cout << endl << "Invalid Input Or Insufficient Balance ";
            _getch();
        }
    }
};

int main() {
    int choice = 0, enterPin;
    long int enterAccountNo;

    system("cls");

    atm user1;
    user1.setData(12345678, "Gaurav", 786786, 1000000, "9053454159");

    do {
        system("cls");
        cout << endl << "---Welcome To The G-ATM---" << endl;
        cout << endl << "Enter Your Account Number : " << endl;
        cin >> enterAccountNo;

        cout << endl << "Enter Your 6-Digit Pin : " << endl;
        cin >> enterPin;

        if ((enterAccountNo == user1.getAccountNumber()) && (enterPin == user1.getPin())) {
            do {
                int amount = 0;
                string oldMobileNo, newMobileNo;
                system("cls");

                cout << endl << "---Welcome To The G-ATM---" << endl;
                cout << endl << "Select Options : ";
                cout << endl << "1. Check Balance ";
                cout << endl << "2. Cash Withdrawal ";
                cout << endl << "3. Show User Details ";
                cout << endl << "4. Update Mobile No. ";
                cout << endl << "5. Exit "<<endl;
                cin >> choice;

                switch (choice) {
                    case 1:
                        cout << endl << "Your Bank Balance is: " << user1.getBalance();
                        _getch();
                        break;

                    case 2:
                        cout << endl << "Enter the Amount : ";
                        cin >> amount;
                        user1.cashWithDraw(amount);
                        break;

                    case 3:
                        cout << endl << "--User Details Are--";
                        cout << endl << "-> Account Number : " << user1.getAccountNumber();
                        cout << endl << "-> Name : " << user1.getName();
                        cout << endl << "-> Balance : " << user1.getBalance();
                        cout << endl << "-> Mobile No. : " << user1.getMobile_No();
                        _getch();
                        break;

                    case 4:
                        cout << endl << "Enter Your Old Number : ";
                        cin >> oldMobileNo;
                        cout << endl << "Enter New Mobile Number : ";
                        cin >> newMobileNo;
                        user1.setMobile(oldMobileNo, newMobileNo);
                        break;

                    case 5:
                        exit(0);

                    default:
                        cout << endl << "Enter Valid Details !!! ";
                }
            } while (1); // Menu loop
        } else {
            cout << endl << "Incorrect Account Number or Pin. Please try again." << endl;
            _getch();
        }
    } while (1); // Login loop

    return 0;
}
