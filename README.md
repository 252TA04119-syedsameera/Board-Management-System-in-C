#include <stdio.h>

struct Board
{
    int id;
    char name[30];
    char type[30];
    float length;
    float width;
    float price;
    int quantity;
};

void addBoard(struct Board b[], int *n)
{
    printf("\nEnter Board ID: ");
    scanf("%d", &b[*n].id);

    printf("Enter Board Name: ");
    scanf(" %[^\n]", b[*n].name);

    printf("Enter Board Type: ");
    scanf(" %[^\n]", b[*n].type);

    printf("Enter Length (cm): ");
    scanf("%f", &b[*n].length);

    printf("Enter Width (cm): ");
    scanf("%f", &b[*n].width);

    printf("Enter Price: ");
    scanf("%f", &b[*n].price);

    printf("Enter Quantity: ");
    scanf("%d", &b[*n].quantity);

    (*n)++;

    printf("\nBoard added successfully!\n");
}

void displayBoards(struct Board b[], int n)
{
    int i;

    if (n == 0)
    {
        printf("\nNo board records available.\n");
        return;
    }

    printf("\n========== BOARD DETAILS ==========\n");

    for (i = 0; i < n; i++)
    {
        printf("\nBoard %d\n", i + 1);
        printf("ID       : %d\n", b[i].id);
        printf("Name     : %s\n", b[i].name);
        printf("Type     : %s\n", b[i].type);
        printf("Length   : %.2f cm\n", b[i].length);
        printf("Width    : %.2f cm\n", b[i].width);
        printf("Price    : Rs. %.2f\n", b[i].price);
        printf("Quantity : %d\n", b[i].quantity);
    }
}

void searchBoard(struct Board b[], int n)
{
    int id, i, found = 0;

    printf("\nEnter Board ID to search: ");
    scanf("%d", &id);

    for (i = 0; i < n; i++)
    {
        if (b[i].id == id)
        {
            printf("\nBoard Found!\n");
            printf("ID       : %d\n", b[i].id);
            printf("Name     : %s\n", b[i].name);
            printf("Type     : %s\n", b[i].type);
            printf("Length   : %.2f cm\n", b[i].length);
            printf("Width    : %.2f cm\n", b[i].width);
            printf("Price    : Rs. %.2f\n", b[i].price);
            printf("Quantity : %d\n", b[i].quantity);

            found = 1;
            break;
        }
    }

    if (found == 0)
    {
        printf("\nBoard not found.\n");
    }
}

void calculateTotal(struct Board b[], int n)
{
    int i;
    float total = 0;

    for (i = 0; i < n; i++)
    {
        total = total + (b[i].price * b[i].quantity);
    }

    printf("\nTotal value of all boards = Rs. %.2f\n", total);
}

int main()
{
    struct Board b[100];
    int n = 0;
    int choice;

    do
    {
        printf("\n\n================================");
        printf("\n       BOARD MANAGEMENT SYSTEM");
        printf("\n================================");

        printf("\n1. Add Board");
        printf("\n2. Display Boards");
        printf("\n3. Search Board");
        printf("\n4. Calculate Total Value");
        printf("\n5. Exit");

        printf("\n\nEnter your choice: ");
        scanf("%d", &choice);

        switch (choice)
        {
            case 1:
                addBoard(b, &n);
                break;

            case 2:
                displayBoards(b, n);
                break;

            case 3:
                searchBoard(b, n);
                break;

            case 4:
                calculateTotal(b, n);
                break;

            case 5:
                printf("\nThank you!\n");
                break;

            default:
                printf("\nInvalid choice! Try again.\n");
        }

    } while (choice != 5);

    return 0;
}
