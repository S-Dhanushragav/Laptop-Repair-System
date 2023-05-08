# Laptop-Repair-System
Created Laptop repair system using c language on march 2023

Code: -

#include <stdio.h>
#include <stdlib.h>
#include <string.h>

#define MAX_REQUESTS 100

typedef struct 
{
    char name[50];
    char model[50];
    char problem[100];
    char status[20];
} RepairRequest;

RepairRequest requests[MAX_REQUESTS];
int num_requests = 0;

void login();
void register_request();
void check_request();
void update_request();
void display_menu();

int main() {
    login();
    display_menu();
    return 0;
}

void login() 
{
    char username[20];
    char password[20];
    printf("Enter username: ");
    scanf("%s", username);
    printf("Enter password: ");
    scanf("%s", password);
    if (strcmp(username, "admin") != 0 || strcmp(password, "password") != 0) 
	{
        printf("Invalid username or password\n");
        exit(1);
    }
}

void register_request() 
{
    if (num_requests == MAX_REQUESTS) 
	{
        printf("Maximum number of requests reached\n");
        return;
    }
    RepairRequest new_request;
    printf("Enter name: ");
    scanf("%s", new_request.name);
    printf("Enter laptop model: ");
    scanf("%s", new_request.model);
    printf("Enter problem: ");
    scanf("%s", new_request.problem);
    strcpy(new_request.status, "pending");
    requests[num_requests++] = new_request;
    printf("Request registered successfully\n");
}

void check_request() 
{
    char name[50];
    printf("Enter name: ");
    scanf("%s", name);
    int found = 0;
    int i;
    for (i= 0; i < num_requests; i++) 
	{
        if (strcmp(requests[i].name, name) == 0) 
		{
            printf("Name: %s\n", requests[i].name);
            printf("Model: %s\n", requests[i].model);
            printf("Problem: %s\n", requests[i].problem);
            printf("Status: %s\n", requests[i].status);
            found = 1;
            break;
        }
    }
    if (!found) 
	{
        printf("No requests found for name %s\n", name);
    }
}
void update_request() 
{
    char name[50];
    printf("Enter name: ");
    scanf("%s", name);
    int found = 0;
    int i;
        for (i = 0; i < num_requests; i++) 
		{
        if (strcmp(requests[i].name, name) == 0) 
		{
            printf("Enter new status: ");
            scanf("%s", requests[i].status);
            printf("Status updated successfully\n");
            found = 1;
            break;
        }
    }
    if (!found) 
	{
        printf("No requests found for name %s\n", name);
    }
}
void display_menu() 
{
    int choice;
    do {
        printf("\nLaptop Repair System\n");
        printf("1. Register a new request\n");
        printf("2. Check the status of a request\n");
        printf("3. Update the status of a request\n");
        printf("4. Exit\n");
        printf("Enter choice: ");
        scanf("%d", &choice);
        switch (choice) 
		{
            case 1:
                register_request();
                break;
            case 2:
                check_request();
                break;
            case 3:
                update_request();
                break;
            case 4:
                printf("Exiting...\n");
                break;
            default:
                printf("Invalid choice\n");
        }
    } while (choice != 4);
}

Modules: - 
 
1.	Customer request for repair: This module allows customers to request a laptop repair by providing details such as the laptop's model, the problem they are experiencing, and their contact information. The system records this information and assigns the repair request to an available expert. 
2.	Technician diagnoses the laptop: This module enables the assigned technician to diagnose the laptop and determine the cause of the problem. The technician records their diagnosis and creates a repair plan for the laptop. 
3.	Laptop is returned to the customer: This module records the date and time when the repaired laptop is returned to the customer. The system generates a notification to inform the customer that their laptop is ready for pickup. 
4.	Manage customer details: This module allows the admin to add, update, or delete customer details from the system. The admin can input information such as the customer's name, contact information, and repair history to ensure accurate record-keeping. 
5.	Manage warranty details: This module enables the admin to manage warranty details for laptops. The admin can input information such as the warranty period, terms, and conditions to ensure that customers receive the necessary coverage for their repairs. 
6.	Manage report: This module enables the admin to generate reports on customer data, laptop data, and expert data. The reports provide valuable insights into the repair process and enable the admin to make data-driven decisions. 
7.	Assign expert: This module allows the admin to assign an available expert to handle a laptop repair request. The system matches the repair request with an expert who has the required skills and availability. 
8.	Expert details: This module allows the admin to maintain a record of experts who are capable of handling laptop repair requests. The admin can input information such as the expert's name, contact details, and areas of expertise to help assign them to the appropriate repair request. 
9.	Manage system admins: This module enables the admin to manage system admins who have access to the Laptop Repair System. The admin can add, update, or delete system admins and assign different levels of access and permissions. 

