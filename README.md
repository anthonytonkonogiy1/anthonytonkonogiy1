#include <iostream>
#include<cstdlib>
#include<fstream>
#include <string>
using namespace std;

int menu() {
	int choice;
	cout << "Anthony's Phone Book" << endl;
	cout << "option 1) enter contact information" << endl;
	cout << "option 2)Veiw Contacts " << endl;
	cout << "option 3) Exit Phone Book" << endl;
	cout << "enter your choice ";
	cin >> choice;
	return choice;
}

void addContacts() {
	string FirstName;
	string LastName;
	string PhoneNumber;
	int exit = 0;
	while (exit != 2 ){

		cout << "enter the first name and last name of the person you would like to add to your contacts" << endl;
		cin >> FirstName >> LastName;

		cout << "enter the phone number you would like to add" << endl;
		cin >> PhoneNumber;

		ofstream APhonebook;
		APhonebook.open("Phonebook.txt");
		APhonebook << "Full Name " << FirstName << " " << LastName << "Phone #" << PhoneNumber;
		APhonebook.close();


		cout << "would you like to add any more contacts? if yes enter 1, if no enter 2 ";
		cin >> exit;


	}
}

void  veiwContacts() {
	string line;
	ifstream APhonebook("Phonebook.txt");
	if (APhonebook.is_open())
	{

		while (getline(APhonebook, line))
		{
			cout << line << endl;
		}
		APhonebook.close();
	}
	else
		cout << "the phone book is empty" << endl;


}


int main() {
	int option;
	do {
		option = menu();
		switch (option) {
			case 1: addContacts();
				break;
			case 2: veiwContacts();
				break;
			case 3:
				break;
			default: cout << option << " Is not one of the displayed options please pick again" << endl;
	

		}


	} while (option != 3);


}
