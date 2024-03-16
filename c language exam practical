#include <stdio.h>
#include <string.h>

#define MAX_EMPLOYEES 100
#define FILENAME "employees.txt"

/*
this is the structure which is define with id, name , department , salary.
*/
struct Employee {
    int id;
    char name[100];
    char department[100];
    float salary;
};

/*
this is the function prototyping functions are declare below main function.
*/
int isDuplicateID(struct Employee employees[], int count, int id);
int isValidID(int id);
void addRecord(struct Employee employees[], int *count);
void displayAllRecords(struct Employee employees[], int count);
void searchEmployeeByID(struct Employee employees[], int count, int id);
void updateEmployeeByID(struct Employee employees[], int count, int id);
void deleteEmployeeByID(struct Employee employees[], int *count, int id);
float calculateTotalSalary(struct Employee employees[], int count);
void generateReportByDepartment(struct Employee employees[], int count, char department[]);
void exitProgram();
void saveDataToFile(struct Employee employees[], int count);
void loadDataFromFile(struct Employee employees[], int *count);





int main() {
    struct Employee employees[MAX_EMPLOYEES];
    int count = 0;
    int choice;
    int id;
    char department[100];

    loadDataFromFile(employees, &count);

    do {
        printf("\nEmployee Management System\n");
        printf("1. Add a new record\n");
        printf("2. Display all records\n");
        printf("3. Search employee by ID\n");
        printf("4. Update employee details by ID\n");
        printf("5. Delete an employee record\n");
        printf("6. Calculate total salary of all employees\n");
        printf("7. Generate a report of employees in a specific department\n");
        printf("8. Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);

        switch (choice) {
            case 1:
                addRecord(employees, &count);
                break;
            case 2:
                displayAllRecords(employees, count);
                break;
            case 3:
                printf("Enter employee ID: ");
                scanf("%d", &id);
                searchEmployeeByID(employees, count, id);
                break;
            case 4:
                printf("Enter employee ID: ");
                scanf("%d", &id);
                updateEmployeeByID(employees, count, id);
                break;
            case 5:
                printf("Enter employee ID: ");
                scanf("%d", &id);
                deleteEmployeeByID(employees, &count, id);
                break;
            case 6:
                printf("Total salary of all employees: %.2f\n", calculateTotalSalary(employees, count));
                break;
            case 7:
                printf("Enter department name: ");
                scanf("%s", department);
                generateReportByDepartment(employees, count, department);
                break;
            case 8:
                saveDataToFile(employees, count);
                exitProgram();
                break;
            default:
                printf("Invalid choice. Please enter a number between 1 and 8.\n");
        }
    } while (choice != 8);

    return 0;
}

int isDuplicateID(struct Employee employees[], int count, int id) {
    for (int i = 0; i < count; i++) {
    
        if (employees[i].id == id) {
          // agar id same hai toh
            return 1; 
        }
    }
  // agar id same nai hai toh
    return 0; 
}

int isValidID(int id) {
  // sirf positive value integer hi lena hai
    return id > 0; 
}

void addRecord(struct Employee employees[], int *count) {
    if (*count < MAX_EMPLOYEES) {
        struct Employee emp;
        printf("Enter employee ID: ");
        scanf("%d", &emp.id);
        
        if (!isValidID(emp.id)) {
            printf("Invalid ID. Please enter a positive integer.\n");
            return;
        }

        if (isDuplicateID(employees, *count, emp.id)) {
            printf("Duplicate ID found. Please enter a unique ID.\n");
            return;
        }

        printf("Enter employee name: ");
        scanf("%s", emp.name);
        printf("Enter employee department: ");
        scanf("%s", emp.department);
        printf("Enter employee salary: ");
        scanf("%f", &emp.salary);
        employees[*count] = emp;
        (*count)++;
        printf("Record added successfully.\n");
    } else {
        printf("Maximum number of employees reached. Cannot add more records.\n");
    }
}

void displayAllRecords(struct Employee employees[], int count) {
    if (count == 0) {
        printf("No records found.\n");
    } else {
        printf("Employee Records:\n");
        for (int i = 0; i < count; i++) {
            printf("ID: %d, Name: %s, Department: %s, Salary: %.2f\n",
                   employees[i].id, employees[i].name, employees[i].department, employees[i].salary);
        }
    }
}

void searchEmployeeByID(struct Employee employees[], int count, int id) {
    int found = 0;
    for (int i = 0; i < count; i++) {
        if (employees[i].id == id) {
            printf("Employee found:\n");
            printf("ID: %d, Name: %s, Department: %s, Salary: %.2f\n",
                   employees[i].id, employees[i].name, employees[i].department, employees[i].salary);
            found = 1;
            break;
        }
    }
    if (!found) {
        printf("Employee with ID %d not found.\n", id);
    }
}

void updateEmployeeByID(struct Employee employees[], int count, int id) {
    int found = 0;
    for (int i = 0; i < count; i++) {
        if (employees[i].id == id) {
            printf("Enter new name: ");
            scanf("%s", employees[i].name);
            printf("Enter new department: ");
            scanf("%s", employees[i].department);
            printf("Enter new salary: ");
            scanf("%f", &employees[i].salary);
            printf("Employee details updated successfully.\n");
            found = 1;
            break;
        }
    }
    if (!found) {
        printf("Employee with ID %d not found.\n", id);
    }
}

void deleteEmployeeByID(struct Employee employees[], int *count, int id) {
    int found = 0;
    for (int i = 0; i < *count; i++) {
        if (employees[i].id == id) {
            for (int j = i; j < *count - 1; j++) {
                employees[j] = employees[j + 1];
            }
            (*count)--;
            printf("Employee with ID %d deleted successfully.\n", id);
            found = 1;
            break;
        }
    }
    if (!found) {
        printf("Employee with ID %d not found.\n", id);
    }
}

float calculateTotalSalary(struct Employee employees[], int count) {
    float totalSalary = 0;
    for (int i = 0; i < count; i++) {
        totalSalary += employees[i].salary;
    }
    return totalSalary;
}

void generateReportByDepartment(struct Employee employees[], int count, char department[]) {
    int found = 0;
    printf("Employee Report for Department: %s\n", department);
    for (int i = 0; i < count; i++) {
        if (strcmp(employees[i].department, department) == 0) {
            printf("ID: %d, Name: %s, Department: %s, Salary: %.2f\n",
                   employees[i].id, employees[i].name, employees[i].department, employees[i].salary);
            found = 1;
        }
    }
    if (!found) {
        printf("No employees found in department %s.\n", department);
    }
}

void exitProgram() {
    printf("Exiting the program.\n");
}

void saveDataToFile(struct Employee employees[], int count) {
    FILE *file = fopen(FILENAME, "w");
    if (file != NULL) {
        for (int i = 0; i < count; i++) {
            fprintf(file, "%d %s %s %.2f\n", employees[i].id, employees[i].name, employees[i].department, employees[i].salary);
        }
        fclose(file);
        printf("Data saved to file successfully.\n");
    } else {
        printf("Error: Unable to open file for writing.\n");
    }
}

void loadDataFromFile(struct Employee employees[], int *count) {
    FILE *file = fopen(FILENAME, "r");
    if (file != NULL) {
        while ((*count < MAX_EMPLOYEES) && fscanf(file, "%d %s %s %f", &employees[*count].id, employees[*count].name,employees[*count].department, &employees[*count].salary) != EOF) {
            (*count)++;
        }
        fclose(file);
        printf("Data loaded from file successfully.\n");
    } else {
        printf("No existing data file found.\n");
    }
}
