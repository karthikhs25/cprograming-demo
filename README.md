#include <stdio.h> 
// Define the structure for a student 
struct Student  
{ 
}; 
int studentID; 
char name[50]; 
char grade; 
float marks[5]; 
float averageMarks; 
// Function to calculate the average marks for a student 
void calculateAverage(struct Student *student)  
{ 
float totalMarks = 0.0; 
for (int i = 0; i < 5; i++)  
{ 
totalMarks += student->marks[i]; 
} 
student->averageMarks = totalMarks / 5; 
} 
// Function to assign grades based on average marks 
void assignGrades(struct Student *student)  
{ 
if (student->averageMarks >= 90)  
 { 
        student->grade = 'A'; 
    }  
    else if (student->averageMarks >= 80)  
    { 
        student->grade = 'B'; 
    }  
    else if (student->averageMarks >= 70)  
    { 
        student->grade = 'C'; 
    }  
    else if (student->averageMarks >= 60)  
    { 
        student->grade = 'D'; 
    }  
    else  
    { 
        student->grade = 'F'; 
    } 
} 
 
int main()  
{ 
    struct Student students[5]; 
    struct Student *studentPtr = students; 
 for (int i = 0; i < 5; i++)  
    { 
        printf("Enter Student ID: "); 
        scanf("%d", &studentPtr->studentID); 
        printf("Enter Name: "); 
        scanf("%s", studentPtr->name); 
        printf("Enter marks for 5 subjects:\n"); 
        for (int j = 0; j < 5; j++)  
        { 
            printf("Subject %d: ", j + 1); 
            scanf("%f", &studentPtr->marks[j]); 
        } 
       // Calculate average marks and assign grades 
        calculateAverage(studentPtr); 
        assignGrades(studentPtr); 
      // Move to the next student in the array 
         studentPtr++; 
        } 
// Reset the pointer to the beginning of the array 
studentPtr = students; 
// Display student information 
printf("\nStudent Information:\n"); 
for (int i = 0; i < 5; i++)  
{ 
printf("Student ID: %d\n", studentPtr->studentID); 
printf("Name: %s\n", studentPtr->name); 
printf("Average Marks: %.2f\n", studentPtr->averageMarks); 
printf("Grade: %c\n", studentPtr->grade); 
printf("\n"); 
// Move to the next student in the array 
studentPtr++; 
} 
return 0; 
}


//program2

#include <stdio.h> 
#include <stdlib.h> 
// Define a structure for a node in the linked list 
struct Node { 
int data; 
struct Node* next; 
}; 
// Define a structure for the stack 
struct Stack { 
struct Node* top; 
}; 
// Function to create an empty stack 
struct Stack* createStack() { 
struct Stack* stack = (struct Stack*)malloc(sizeof(struct Stack)); 
stack->top = NULL; 
return stack; 
} 
// Function to check if the stack is empty 
int isEmpty(struct Stack* stack) { 
return (stack->top == NULL); 
} 
// Function to push an element onto the stack 
void push(struct Stack* stack, int data) { 
struct Node* newNode = (struct Node*)malloc(sizeof(struct Node)); 
newNode->data = data; 
newNode->next = stack->top; 
stack->top = newNode; 
printf("%d pushed to the stack\n", data); 
} 
// Function to pop an element from the stack 
int pop(struct Stack* stack) { 
if (isEmpty(stack)) { 
printf("Stack is empty. Cannot pop.\n");  
return -1; // Return an invalid value 
} 
struct Node* temp = stack->top; 
int poppedData = temp->data; 
stack->top = temp->next; 
free(temp); 
return poppedData; 
} 
int main() { 
struct Stack* stack = createStack(); 
push(stack, 10); 
push(stack, 20); 
push(stack, 30); 
printf("%d popped from the stack\n", pop(stack)); 
printf("%d popped from the stack\n", pop(stack)); 
printf("%d popped from the stack\n", pop(stack)); 
printf("%d popped from the stack\n", pop(stack)); // Trying to pop from an empty stack 
return 0; 
}
