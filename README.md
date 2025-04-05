#include <stdio.h>

struct contact{

    char name[100],phone[100],email[100];

};

void addcontact()
{
    FILE *file;
    file = fopen("contact.txt","a");
    if(file==NULL)
    {
        printf("File does not exist.");
    }else{
        printf("File is opened\n");
      struct contact contact;
    fflush(stdin);
    printf("Enter Name : ");
    fgets(contact.name,sizeof(contact.name),stdin);

    printf("Enter Phone : ");
    fgets(contact.phone,sizeof(contact.phone),stdin);

    printf("Enter Email : ");
    fgets(contact.email,sizeof(contact.email),stdin);

    fprintf(file,"%s %s %s \n",contact.name,contact.phone,contact.email);

    fclose(file);
    printf("Added to contact management system : ");
    }
}
void displaycontacts()
{
    struct contact contact;
    FILE *file;
    file = fopen("contact.txt","r");
    if(file==NULL)
    {
        printf("File does not exist.");
    }else{

        printf("contacts.\n");


    while(fscanf(file," %[^\n] %[^\n] %[^\n]",contact.name,contact.phone,contact.email)!=EOF)
    {
        printf("Name :%s\nphone :%s\nemail :%s\n\n",contact.name,contact.phone ,contact.email);
    }

    fclose(file);

    }
}

int main(){


    int choice;
    do{
        printf("\ncontact management system.\n");
        printf("1.Add contact:\n");
        printf("2.Display contacts:\n");
        printf("3.Exit\n:");

        printf("Enter your choice :");
        scanf("%d",&choice);

        switch(choice)
        {
            case 1:
            addcontact();
            break;
            case 2:
            displaycontacts();
            break;
            case 3:
            printf("Existing...\n");
            break;
            default:
            printf("Invalid choice.please try again.\n");

        }

    }while(choice!=3);
}
