# student-management-system-in-c

Student management system is a entry level project for all cse Student.if any student student start study  bsc in  cse than this project perfect for a first semester student as a project 1

** This the Welcome Screen **
```
int main()
{
     printf("\n\n\n\n\n");
    printf("\n\t\t\t  **-**-**-**-**-**-**-**-**-**-**-**-**-**-**-**-**-**-**\n");
    printf("\n\t\t\t        =-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=");
    printf("\n\t\t\t        =                  WELCOME                  =");
    printf("\n\t\t\t        =                    TO                     =");
    printf("\n\t\t\t        =                   SMUCT                   =");
    printf("\n\t\t\t        =                  STUDENT                  =");
    printf("\n\t\t\t        =                 MANAGEMENT                =");
    printf("\n\t\t\t        =                   SYSTEM                  =");
    printf("\n\t\t\t        =-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=");
    printf("\n\t\t\t  **-**-**-**-**-**-**-**-**-**-**-**-**-**-**-**-**-**-**\n");
    printf("\n\n\n\t\t\t Enter any key to continue.....");
    getch();
    menu();
}
```
# Here is the function use in project

## Here 5 menu item and its work with switch stetment .

```
void menu()
{
    int uc;
     printf("\t\t\t##########################################################");
    printf("\n\t\t\t############                MENU             ############");
    printf("\n\t\t\t#########################################################");
    printf("\n\t\t\t############     ENTER A NUMBER FOR         #############");
    printf("\n\n");
    printf("                         1.student adding\n\n");
    printf("                         2.view student details\n\n");
    printf("                         3.search student details\n\n");
    printf("                         4.delete student details \n\n");
    printf("                         5.For exit\n");
    printf("                         Enter your choice \n\n");
    scanf("%d",&uc);
    switch(uc)
    {
    case 1:
        add();
        break;
    case 2:
        view();
        break;
    case 3:
        search();
        break;
    case 4:
        del();
        break;
    case 5:
        exit(1);
        break;

    default:
        printf("wrong choice.please try again.");


    }
}
``` 
This is add Faunction for add data

```
    void add()
    {
        FILE *fptr;
        struct student std;
        char another='Y';
        fptr=fopen("record.txt","ab+");
        if(fptr==NULL){
            printf("Error opening file");
        exit(1);
    }
    fflush(stdin);
    while(another=='Y')
    {
        printf("                          ########### Adding student details################\n");

        printf("    \t\t\t\t\t  Enter student name:\n");

        gets(std.name);
        printf("    \t\t\t\t\t  Enter student id:\n");

        gets(std.id);
        printf("      \t\t\t\t\t   Enter student depertment \n");


        gets(std.dept);
        fwrite(&std,sizeof(std),1,fptr);


        printf("\t\t\t\t\t  Want to add of another record? Then press 'y' else 'n'.");
        fflush(stdin);
        another = getch();
        fflush(stdin);

    }
    fclose(fptr);
    printf("Press any key to continue....");
    getch();
    menu();

}
```

This is the function for show exgisting data 
```
void view()
{
    FILE *fp;
    int i=1,j;
    struct student std;

    printf("                            ###### VIEW STUDENT DETAILS#####\n");

    printf("-----------------------------------------------------------------------------------------\n");
    fp = fopen("record.txt","rb+");
    if(fp == NULL)
        {
        printf("Error opening file.");
        exit(1);
       }

      j=8;

    while(fread(&std,sizeof(std),1,fp) == 1)
        {
        printf("\t\t\t\t\t%d.%s\n\n\t\t\t\t\tID:%s\n\n\t\t\t\t\tDEPT:%s\n  \n\n",i,std.name,std.id,std.dept);
        i++;
        j++;
    }
    fclose(fp);
    printf("              Press any key to continue.");
    getch();
    menu();
}
```
This is Search Function 
```
void search()
{
    FILE *fp;
    struct student std;
    char stname[20];

    printf("           ###### SRESRCH STUDENT DETAILS#####\n\n");
    printf("    \t\t\t\t\t  Enter name of student : ");
    fflush(stdin);
    gets(stname);
    fp = fopen("record.txt","rb+");
    if(fp == NULL)
        {
        printf("Error opening file");
        exit(1);
        }

    while(fread(&std,sizeof(std),1,fp ) == 1){
        if(strcmp(stname,std.name) == 0){
            printf("         Name : %s\n",std.name);


            printf("         Student id: %s\n",std.id);

            printf("          depertment  : %s\n",std.dept);


        }
    }
    fclose(fp);

    printf("Press any key to continue....");
    getch();
    menu();
}
```
This Function use for data delete

```
void del()
{
        char stname[20];
    FILE *fp,*ft;
    struct student std;
    system("cls");

    printf("              ######DELETE STUDENT DETAILS####\n\n");

    printf("              Enter name of student to delete details : ");
    fflush(stdin);

    gets(stname);

    fp = fopen("record.txt","rb+");
    if(fp == NULL)
    {

        printf("Error opening file");
        exit(1);
    }
    ft = fopen("temp.txt","wb+");
    if(ft == NULL)
    {
        printf("Error opening file");
        exit(1);
    }
    while(fread(&std,sizeof(std),1,fp) == 1){
        if(strcmp(stname,std.name)!=0)
            fwrite(&std,sizeof(std),1,ft);
    }
    fclose(fp);
    fclose(ft);
    remove("record.txt");
    rename("temp.txt","record.txt");

    printf("Press any key to continue.");
    getch();
    menu();
}
```

i will try to code with very simple way .
** if any kind of query knock me in facebook**

#Thank you .......
