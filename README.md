# lINKEDLISTSORT
SORTS DATA IN LINKED LIST 
// ConsoleApplication7.cpp : Write a program USING LINKED LIST to sort a student data file. 
// Jonathan Sessom

#include <iostream>
#include <fstream>
#include <string>
#include <stdlib.h>
using namespace std;




struct node // Linked list
{
	int id;
	float gpa;
	string name;
	int index;
	node *next;
};

struct node2
{
	int id;
	int index;
};


bool isEmpty(node *head)
{
	if (head == NULL)
		return true;
	else
		return false;

}
char menu()
{
	char choice;
	cout << "Menu\n";
	cout<< "1. Add an item.\n";
	cout << "2. Remove an item.\n";
	cout << "3. Show the list.\n";
	cout << "4. Exit.\n";
	
	cin >> choice;
	return choice;
}

void insertasFirstElement(node *&head, node *&last, string name, int id, float gpa)
{
	node *temp = new node;
	//node *temp;
	//temp = (struct node*)malloc(sizeof(struct node));

	temp->name = name;
	temp->id = id;
	temp->gpa = gpa;
	temp->next = NULL;
	head = temp;
	last = temp;

}



void insertion(node *&head, node *&last, string name, int id, float gpa)
{
	if (isEmpty(head))
		insertasFirstElement(head, last, name , id, gpa);
	else
	{
		
		node *temp = new node;
		//node *temp;
		//temp = (struct node*)malloc(sizeof(struct node));
		
		temp->name = name;
		temp->id = id;
		temp->gpa = gpa;
		temp->next = NULL;
		last->next = temp;
		last = temp;
		

	}

}
void remove(node *head, node *last)
{
	if (isEmpty(head))
		cout << "The list is empty. \n";
	else if (head == last)
	{
		delete head;
		head == NULL;
		last == NULL;
	}
	else
	{
		node *temp = head;
		head = head -> next;
		delete temp;
	}
}

void showList(node *current)
{
	if (isEmpty(current))
		cout << " The list is empty. \n";
	else
	{
		cout << " The linked list contains: \n";
		while (current != NULL)
		{

			cout << current->id<<"		";
			//cout<<		 current->gpa << "		 " ; 
			//cout<<current->name<<"		"<<endl;
			cout << endl;
			current = current->next;


		}
	}
}

void sortLinkedList(node *head)
{
	

	node *i, *j;
	j = head;

	for (j = head; j != NULL; j = j->next)//Passes
	{
		for (i = j->next; i != NULL; i = i->next)
		{
			// initialization
			
			node *temp = new node;
			node *next = 0;
			
			if (i->id < j->id)
			{
				int temp; 
				
				

				temp = i->id;

				i->id = j->id;

				j->id = temp;
				

			}
			
		
		}
	}

}






int main()
{
	node *head = NULL;
	node *last = NULL;
	node *next = 0;
	char choice;
	int id;
	float gpa = 0.0;
	string name;
	ifstream inputfile;
	inputfile.open("Z:\\CS-246\\ConsoleApplication5\\Studentdatafile.txt");

	if (!inputfile)
	{
		cerr << "File is not open." << endl;
		exit(1);
	}

	
	for (int i =0; i < 10; i++)
	{
		

				inputfile >> name;
				
				inputfile >> id;
				
				inputfile>> gpa;
				cout << endl;
				insertion(head, last, name, id, gpa);
				showList(head);
	} 
	
	sortLinkedList(head);
	showList(head);

	return 0;
}
