//# fusiotech-internship //
rock paper scissor game
#include <math.h>
#include <stdio.h>
#include <stdlib.h>
#include <time.h>
 
// Function to implement the game
int game(char you, char computer)
{
    // If both the user and computer
    // has choose the same thing
    if (you == computer)
        return -1;
 
    // If user's choice is stone and
    // computer's choice is paper
    if (you == 's' && computer == 'p')
        return 0;
 
            // If user's choice is paper and
            // computer's choice is stone
            else if (you == 'p' && computer == 's') return 1;
 
    // If user's choice is stone and
    // computer's choice is scissor
    if (you == 's' && computer == 'z')
        return 1;
 
    // If user's choice is scissor and
    // computer's choice is stone
    else if (you == 'z' && computer == 's')
        return 0;
 
    // If user's choice is paper and
    // computer's choice is scissor
    if (you == 'p' && computer == 'z')
        return 0;
 
    // If user's choice is scissor and
    // computer's choice is paper
    else if (you == 'z' && computer == 'p')
        return 1;
}
 
// Driver Code
int main()
{
    // Stores the random number
    int n;
 
    char you, computer, result;
 
    // Chooses the random number
    // every time
    srand(time(NULL));
 
    // Make the random number less
    // than 100, divided it by 100
    n = rand() % 100;
 
    // Using simple probability 100 is
    // roughly divided among stone,
    // paper, and scissor
    if (n < 33)
 
        // s is denoting Stone
        computer = 's';
 
    else if (n > 33 && n < 66)
 
        // p is denoting Paper
        computer = 'p';
 
    // z is denoting Scissor
    else
        computer = 'z';
 
    printf("\n\n\n\n\t\t\t\tEnter s for STONE, p for PAPER and z for SCISSOR\n\t\t\t\t\t\t\t");
 
    // input from the user
    scanf("%c", &you);
 
    // Function Call to play the game
    result = game(you, computer);
 
    if (result == -1) {
        printf("\n\n\t\t\t\tGame Draw!\n");
    }
    else if (result == 1) {
        printf("\n\n\t\t\t\tWow! You have won the game!\n");
    }
    else { 
        printf("\n\n\t\t\t\tOh! You have lost the game!\n");
    }
        printf("\t\t\t\tYOu choose : %c and Computer choose : %c\n",you, computer);
 
    return 0;
}










calculator


#include<stdio.h>
#include<math.h>

int main() {
    char op;
    double num1, num2, result;

    while (1) {
       
        printf("Enter an operator (+, -, *, /) or 's' to square root or 'l' to log10 values or 'q' to quit: ");
        scanf(" %c", &op);

        
        if (op == 'q' || op == 'Q') {
            printf("Calculator program is quitting.\n");
            break;
        }
		if(op == 'l')
		{
			printf("Enter number: ");
        	scanf("%lf", &num1);
			result = log10(num1);
			printf("Result: %lf\n", result);
			continue;
		} 
		if(op == 's')
		{
			printf("Enter number: ");
        	scanf("%lf", &num1);
			result = sqrt(num1);
			printf("Result: %lf\n", result);
			continue;
		} 
        
        printf("Enter two numbers: ");
        scanf("%lf %lf", &num1, &num2);

        
        if (op == '+') {
            result = num1 + num2;
        } else if (op == '-') {
            result = num1 - num2;
        } else if (op == '*') {
            result = num1 * num2;
        } else if (op == '/') {
            
            if (num2 != 0) {
                result = num1 / num2;
            } else {
                printf("Error: Division by zero is not allowed.\n");
                continue;  
            }
		}
		
		else {
            printf("Error: Invalid operator. Please enter +, -, *, or /.\n");
            continue;  
        }

        
        printf("Result: %lf\n", result);
    }

    return 0;
}








bank system




// C program to implement
// the above approach
#include <conio.h>
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <windows.h>
 
// Declaring all the functions
void checkbalance(char*);
void transfermoney(void);
void display(char*);
void person(char*);
void login(void);
void loginsu(void);
void account(void);
void accountcreated(void);
void afterlogin(void);
void logout(void);
 
// Declaring gotoxy
// function for setting
// cursor position
void gotoxy(int x, int y)
{
    COORD c;
    c.X = x;
    c.Y = y;
 
    SetConsoleCursorPosition(
        GetStdHandle(STD_OUTPUT_HANDLE), c);
}
 
// Creating a structure to store
// data of the user
struct pass {
    char username[50];
    int date, month, year;
    char pnumber[15];
    char adharnum[20];
    char fname[20];
    char lname[20];
    char fathname[20];
    char mothname[20];
    char address[50];
    char typeaccount[20];
};
 
// Structure to keep track
// of amount transfer
struct money {
    char usernameto[50];
    char userpersonfrom[50];
    long int money1;
};
 
struct userpass {
    char password[50];
};
 
// Driver Code
int main()
{
    int i, a, b, choice;
    int passwordlength;
 
    gotoxy(20, 3);
 
    // Creating a Main
    // menu for the user
    printf("WELCOME TO BANK ACCOUNT SYSTEM\n\n");
    gotoxy(18, 5);
 
    printf("**********************************");
    gotoxy(25, 7);
 
    printf("DEVELOPER-Jeet Varshney");
 
    gotoxy(20, 10);
    printf("1.... CREATE A BANK ACCOUNT");
 
    gotoxy(20, 12);
    printf("2.... ALREADY A USER? SIGN IN");
    gotoxy(20, 14);
    printf("3.... EXIT\n\n");
 
    printf("\n\nENTER YOUR CHOICE..");
 
    scanf("%d", &choice);
 
    switch (choice) {
    case 1:
        system("cls");
        printf("\n\n USERNAME 50 CHARACTERS MAX!!");
        printf("\n\n PASSWORD 50 CHARACTERS MAX!!");
        account();
        break;
 
    case 2:
        login();
        break;
 
    case 3:
        exit(0);
        break;
 
        getch();
    }
}
 
// Function to create accounts
// of users
void account(void)
{
    char password[20];
    int passwordlength, i, seek = 0;
    char ch;
    FILE *fp, *fu;
    struct pass u1;
    struct userpass p1;
 
    struct userpass u2;
 
    // Opening file to
    // write data of a user
    fp = fopen("username.txt", "ab");
 
    // Inputs
    system("cls");
    printf("\n\n!!!!!CREATE ACCOUNT!!!!!");
 
    printf("\n\nFIRST NAME..");
    scanf("%s", &u1.fname);
 
    printf("\n\n\nLAST NAME..");
    scanf("%s", &u1.lname);
 
    printf("\n\nFATHER's NAME..");
    scanf("%s", &u1.fathname);
 
    printf("\n\nMOTHER's NAME..");
    scanf("%s", &u1.mothname);
 
    printf("\n\nADDRESS..");
    scanf("%s", &u1.address);
 
    printf("\n\nACCOUNT TYPE");
    scanf("%s", &u1.typeaccount);
 
    printf("\n\nDATE OF BIRTH..");
    printf("\nDATE-");
    scanf("%d", &u1.date);
    printf("\nMONTH-");
    scanf("%d", &u1.month);
    printf("\nYEAR-");
    scanf("%d", &u1.year);
 
    printf("\n\nADHAR NUMBER");
    scanf("%s", u1.adharnum);
 
    printf("\n\nPHONE NUMBER");
    scanf("%s", u1.pnumber);
 
    printf("\n\nUSERNAME.. ");
    scanf("%s", &u1.username);
 
    printf("\n\nPASSWORD..");
 
    // Taking password in the form of
    // stars
    for (i = 0; i < 50; i++) {
        ch = getch();
        if (ch != 13) {
            password[i] = ch;
            ch = '*';
            printf("%c", ch);
        }
        else
            break;
    }
 
    // Writing to the file
    fwrite(&u1, sizeof(u1),
           1, fp);
 
    // Closing file
    fclose(fp);
 
    // Calling another function
    // after successful creation
    // of account
    accountcreated();
}
 
// Successful account creation
void accountcreated(void)
{
    int i;
    char ch;
    system("cls");
    printf(
        "PLEASE WAIT....\n\nYOUR DATA IS PROCESSING....");
    for (i = 0; i < 200000000; i++) {
        i++;
        i--;
    }
 
    gotoxy(30, 10);
 
    printf("ACCOUNT CREATED SUCCESSFULLY....");
    gotoxy(0, 20);
 
    printf("Press enter to login");
 
    getch();
    login();
}
 
// Login function to check
// the username of the user
void login(void)
{
    system("cls");
 
    char username[50];
    char password[50];
 
    int i, j, k;
    char ch;
    FILE *fp, *fu;
    struct pass u1;
    struct userpass u2;
 
    // Opening file of
    // user data
    fp = fopen("username.txt",
               "rb");
 
    if (fp == NULL) {
        printf("ERROR IN OPENING FILE");
    }
    gotoxy(34, 2);
    printf(" ACCOUNT LOGIN ");
    gotoxy(7, 5);
    printf("***********************************************"
           "********************************");
 
    gotoxy(35, 10);
    printf("==== LOG IN ====");
 
    // Take input
    gotoxy(35, 12);
    printf("USERNAME.. ");
    scanf("%s", &username);
 
    gotoxy(35, 14);
    printf("PASSWORD..");
 
    // Input the password
    for (i = 0; i < 50; i++) {
        ch = getch();
        if (ch != 13) {
            password[i] = ch;
            ch = '*';
            printf("%c", ch);
        }
 
        else
            break;
    }
 
    // Checking if username
    // exists in the file or not
    while (fread(&u1, sizeof(u1),
                 1, fp)) {
        if (strcmp(username,
                   u1.username)
            == 0) {
            loginsu();
            display(username);
        }
    }
 
    // Closing the file
    fclose(fp);
}
 
// Redirect after
// successful login
void loginsu(void)
{
    int i;
    FILE* fp;
    struct pass u1;
    system("cls");
    printf("Fetching account details.....\n");
    for (i = 0; i < 20000; i++) {
        i++;
        i--;
    }
 
    gotoxy(30, 10);
    printf("LOGIN SUCCESSFUL....");
    gotoxy(0, 20);
    printf("Press enter to continue");
 
    getch();
}
 
// Display function to show the
// data of the user on screen
void display(char username1[])
{
    system("cls");
    FILE* fp;
    int choice, i;
    fp = fopen("username.txt", "rb");
    struct pass u1;
 
    if (fp == NULL) {
        printf("error in opening file");
    }
 
    while (fread(&u1, sizeof(u1),
                 1, fp)) {
        if (strcmp(username1,
                   u1.username)
            == 0) {
            gotoxy(30, 1);
            printf("WELCOME, %s %s",
                   u1.fname, u1.lname);
            gotoxy(28, 2);
            printf("..........................");
            gotoxy(55, 6);
            printf("==== YOUR ACCOUNT INFO ====");
            gotoxy(55, 8);
            printf("***************************");
            gotoxy(55, 10);
            printf("NAME..%s %s", u1.fname,
                   u1.lname);
 
            gotoxy(55, 12);
            printf("FATHER's NAME..%s %s",
                   u1.fathname,
                   u1.lname);
 
            gotoxy(55, 14);
            printf("MOTHER's NAME..%s",
                   u1.mothname);
 
            gotoxy(55, 16);
            printf("ADHAR CARD NUMBER..%s",
                   u1.adharnum);
 
            gotoxy(55, 18);
            printf("MOBILE NUMBER..%s",
                   u1.pnumber);
 
            gotoxy(55, 20);
            printf("DATE OF BIRTH.. %d-%d-%d",
                   u1.date, u1.month, u1.year);
 
            gotoxy(55, 22);
            printf("ADDRESS..%s", u1.address);
 
            gotoxy(55, 24);
            printf("ACCOUNT TYPE..%s",
                   u1.typeaccount);
        }
    }
 
    fclose(fp);
 
    gotoxy(0, 6);
 
    // Menu to perform different
    // actions by user
    printf(" HOME ");
    gotoxy(0, 7);
    printf("******");
    gotoxy(0, 9);
    printf(" 1....CHECK BALANCE");
    gotoxy(0, 11);
    printf(" 2....TRANSFER MONEY");
    gotoxy(0, 13);
    printf(" 3....LOG OUT\n\n");
    gotoxy(0, 15);
    printf(" 4....EXIT\n\n");
 
    printf(" ENTER YOUR CHOICES..");
    scanf("%d", &choice);
 
    switch (choice) {
    case 1:
        checkbalance(username1);
        break;
 
    case 2:
        transfermoney();
        break;
 
    case 3:
        logout();
        login();
        break;
 
    case 4:
        exit(0);
        break;
    }
}
 
// Function to transfer
// money from one user to
// another
void transfermoney(void)
{
    int i, j;
    FILE *fm, *fp;
    struct pass u1;
    struct money m1;
    char usernamet[20];
    char usernamep[20];
    system("cls");
 
    // Opening file in read mode to
    // read user's username
    fp = fopen("username.txt", "rb");
 
    // Creating a another file
    // to write amount along with
    // username to which amount
    // is going to be transferred
    fm = fopen("mon.txt", "ab");
 
    gotoxy(33, 4);
    printf("---- TRANSFER MONEY ----");
    gotoxy(33, 5);
    printf("========================");
 
    gotoxy(33, 11);
    printf("FROM (your username).. ");
    scanf("%s", &usernamet);
 
    gotoxy(33, 13);
    printf(" TO (username of person)..");
    scanf("%s", &usernamep);
 
    // Checking for username if it
    // is present in file or not
    while (fread(&u1, sizeof(u1),
                 1, fp))
 
    {
        if (strcmp(usernamep,
                   u1.username)
            == 0) {
            strcpy(m1.usernameto,
                   u1.username);
            strcpy(m1.userpersonfrom,
                   usernamet);
        }
    }
    gotoxy(33, 16);
 
    // Taking amount input
    printf("ENTER THE AMOUNT TO BE TRANSFERRED..");
    scanf("%d", &m1.money1);
 
    // Writing to the file
    fwrite(&m1, sizeof(m1),
           1, fm);
 
    gotoxy(0, 26);
    printf(
        "--------------------------------------------------"
        "--------------------------------------------");
 
    gotoxy(0, 28);
    printf(
        "--------------------------------------------------"
        "--------------------------------------------");
 
    gotoxy(0, 29);
    printf("transferring amount, Please wait..");
 
    gotoxy(10, 27);
    for (i = 0; i < 70; i++) {
        for (j = 0; j < 1200000; j++) {
            j++;
            j--;
        }
        printf("*");
    }
 
    gotoxy(33, 40);
    printf("AMOUNT SUCCESSFULLY TRANSFERRED....");
    getch();
 
    // Close the files
    fclose(fp);
    fclose(fm);
 
    // Function to return
    // to the home screen
    display(usernamet);
}
 
// Function to check balance
// in users account
void checkbalance(char username2[])
{
    system("cls");
    FILE* fm;
    struct money m1;
    char ch;
    int i = 1, summoney = 0;
 
    // Opening amount file record
    fm = fopen("mon.txt", "rb");
 
    int k = 5, l = 10;
    int m = 30, n = 10;
    int u = 60, v = 10;
 
    gotoxy(30, 2);
    printf("==== BALANCE DASHBOARD ====");
    gotoxy(30, 3);
    printf("***************************");
    gotoxy(k, l);
    printf("S no.");
    gotoxy(m, n);
    printf("TRANSACTION ID");
    gotoxy(u, v);
    printf("AMOUNT");
 
    // Reading username to
    // fetch the correct record
    while (fread(&m1, sizeof(m1),
                 1, fm)) {
        if (strcmp(username2,
                   m1.usernameto)
            == 0) {
            gotoxy(k, ++l);
            printf("%d", i);
            i++;
            gotoxy(m, ++n);
            printf("%s", m1.userpersonfrom);
 
            gotoxy(u, ++v);
            printf("%d", m1.money1);
            // Adding and
            // finding total money
            summoney = summoney + m1.money1;
        }
    }
 
    gotoxy(80, 10);
    printf("TOTAL AMOUNT");
 
    gotoxy(80, 12);
    printf("%d", summoney);
 
    getch();
 
    // Closing file after
    // reading it
    fclose(fm);
    display(username2);
}
 
// Logout function to bring
// user to the login screen
void logout(void)
{
    int i, j;
    system("cls");
    printf("please wait, logging out");
 
    for (i = 0; i < 10; i++) {
        for (j = 0; j < 25000000; j++) {
            i++;
            i--;
        }
        printf(".");
    }
 
    gotoxy(30, 10);
    printf("Sign out successfully..\n");
 
    gotoxy(0, 20);
    printf("press any key to continue..");
 
    getch();
}






cricket scored board



#include<stdio.h>
#include<stdlib.h>

struct batsman
 {
   char name[25];
   int runs,score,balls,toruns,tobal,ones,twos,threes,fours,sixes;
   int max_six,max_run,max_four;
   float str;

 }pl1[100],pl3;


struct bowler
 {
   char name[25];
   int runsgv,wkttkn,overs;
   int max_w;
   float econ;
 }pl2[100],pl4;


int main()
{
 int plno,choice;
  int i,n,m;
  printf("Enter the Batsman detail:\n");
  printf("Enter the number of batsman:\n");
  scanf("%d",&m);
  for(i=0;i<m;i++)
   {

       printf("Enter name of batsman%d:\n",i+1);
       scanf("%s",pl1[i].name);


       printf("Enter the number of ones scored by player%d:\n ",i+1);
       scanf("%d",&pl1[i].ones);


       printf("Enter the number of twos scored by player%d:\n ",i+1);
       scanf("%d",&pl1[i].twos);


       printf("Enter the number of threes scored by player%d:\n ",i+1);
       scanf("%d",&pl1[i].threes);


       printf("Enter the number of fours scored by player%d:\n ",i+1);
       scanf("%d",&pl1[i].fours);


       printf("Enter the number of sixes scored by player%d:\n ",i+1);
       scanf("%d",&pl1[i].sixes);


       printf("Enter the balls played by the player%d:\n",i+1);
       scanf("%d",&pl1[i].balls);
   }



   printf("\nEnter the bowlers details:\n");

   printf("Enter the number of bowlers:\n");

   scanf("%d",&n);


   for(i=0;i<n;i++)
   {

       printf("\nEnter name of bowler%d:",i+1);
       scanf("%s",pl2[i].name);


       printf("Enter the runs given by the bowler%d:\n ",i+1);
       scanf("%d",&pl2[i].runsgv);


       printf("Enter the overs bowled by the bowler%d:\n",i+1);
       scanf("%d",&pl2[i].overs);


       printf("Enter the wickets taken by the bowler%d\n",i+1);
       scanf("%d",&pl2[i].wkttkn);

   }

   printf("Thank you all details are recorded\n");


   do
    {

       printf("Enter the choice:\n 1)Batsman detail:\n 2)Bowlers detail:\n 3)Match summary:\n 4)Record:\n 5)Exit\n ");
       scanf("%d",&choice);

     switch(choice)
      {

        case 1:
              printf("Enter the batsman number to see his details\n");
              scanf("%d",&plno);

              plno--;
              printf("                       Player Detail\n");
              printf("===========================================================================\n");
              printf(" Batsman        runs           balls        fours       sixes         sr   \n");
              printf("===========================================================================\n");


              pl1[plno].runs=(1*pl1[plno].ones)+(2*pl1[plno].twos)+(3*pl1[plno].threes)+(4*pl1[plno].fours)+(6*pl1[plno].sixes);
              pl1[plno].str=(pl1[plno].runs*100.00)/pl1[plno].balls;
              printf(" %-15s %-14d %-13d %-11d %-11d %-9.2f\n\n",pl1[plno].name,pl1[plno].runs,pl1[plno].balls,pl1[plno].fours,pl1[plno].sixes,pl1[plno].str);

              break;


        case 2:
             printf("Enter the bowlers number to see his details\n");
             scanf("%d",&plno);

             plno--;
              printf("                         Player Detail\n  ");
              printf("=================================================================\n");
              printf(" Bowler        overs           runs        wicket       economy\n");
              printf("=================================================================\n");

               for(i=0;i<n;i++)
               {   pl2[plno].econ=pl2[plno].runsgv/pl2[plno].overs;
                   printf(" %-15s %-14d %-13d %-11d %-11.2f\n\n",pl2[plno].name,pl2[plno].overs,pl2[plno].runsgv,pl2[plno].wkttkn,pl2[plno].econ);
               }

             break;

        case 3:
              printf("                     Match summary\n");
              printf("==========================================================================\n");
              printf(" Batsman        runs           balls        fours       sixes         sr   \n");
              printf("==========================================================================\n");

              for(i=0;i<1;i++)
                {
                    pl1[i].runs=(1*pl1[i].ones)+(2*pl1[i].twos)+(3*pl1[i].threes)+(4*pl1[i].fours)+(6*pl1[i].sixes);
                    pl3.toruns+=pl1[i].runs;
                    pl1[i].str=(pl1[i].runs*100.00)/pl1[i].balls;
                    printf(" %-15s %-14d %-13d %-11d %-11d %-9.2f\n\n",pl1[i].name,pl1[i].runs,pl1[i].balls,pl1[i].fours,pl1[i].sixes,pl1[i].str);
                }
                printf("TOTAL RUNS:%d\n\n",pl3.toruns);
              printf("\n\n");
              printf("=================================================================\n");
              printf(" Bowler        overs           runs        wicket       economy\n");
              printf("=================================================================\n");

               for(i=0;i<n;i++)
               {   pl2[i].econ=pl2[i].runsgv/pl2[i].overs;
                   printf(" %-15s %-14d %-13d %-11d %-11.2f\n\n\n",pl2[i].name,pl2[i].overs,pl2[i].runsgv,pl2[i].wkttkn,pl2[i].econ);
               }


               break;

        case 4: pl3.max_run=0,pl4.max_w=0,pl3.max_four=0,pl3.max_six=0;
       
                for(i=0;i<m;i++)
                  { 
                     pl1[i].runs=(1*pl1[i].ones)+(2*pl1[i].twos)+(3*pl1[i].threes)+(4*pl1[i].fours)+(6*pl1[i].sixes);
                     if(pl3.max_run<pl1[i].runs)
                        {
                          pl3.max_run=pl1[i].runs;

                        }
                 
                     if(pl3.max_six<pl1[i].sixes)
                       {
                        pl3.max_six=pl1[i].sixes;
                       }
                 
                     if(pl3.max_four<pl1[i].fours)
                       {
                        pl3.max_four=pl1[i].fours;
                       }
 
                     if(pl4.max_w<pl2[i].wkttkn)
                      {
                      pl4.max_w=pl2[i].wkttkn;
                      }
                  }
              printf("Highest runs scored by the batsman:%d\n",pl3.max_run);
   
              printf("Maximum fours scored by the batsman:%d\n",pl3.max_four);

              printf("Maximum sixes scored by the batsman%d:\n",pl3.max_six);
 
             printf("Maximum wickets taken by the bowler:%d\n",pl4.max_w);

             break;



        case 5:
            exit(1);

        default:
             printf("Enter the correct choice\n");
             break;

      }

    }while(choice!=5);


   return 0;

}










number system change




/*
  Project Name: Number System Converter 
  Created By: JEET VARSHNEY
  
  
*/
#include<stdio.h>  // for: input & output 
#include<stdlib.h> // for: exit(0) function 
#include<conio.h>  // for: getch() function 
#include<ctype.h>  // for: isdigit() function 
#include<math.h>   // for: pow(2,0) function 
#include<string.h> // for: strlen() function

// Define Constant KeyWords: for tracking user key press event (used in: HexaDecimal input validation) 
#define ENTER 13
#define TAB 9
#define BKSP 8

void welcomeScreen(void);    // Introduction Page & choice screen 
void exitScreen(void);       // program end screen with credits 
void screenCleaner(void);    // clears the output screen and input buffers 
void userInput(int);         // takes the user input and validates for further opertaions 
int digitChecker(int, int);  // validates each digit of input number 
void conversion_Title(void); // title for all conversion outputs 
void tryAgain(int);          // try Again window 

// Binary Conversion functions 
void binary_decimal(long int);
void binary_octal(long int);
void binary_hexadecimal(long int);

// Decimal Conversion functions 
void decimal_binary(long int);
void decimal_octal(long int);
void decimal_hexadecimal(long int);

// Octal Conversion functions 
void octal_binary(long int);
void octal_decimal(long int);
void octal_hexadecimal(long int);

// Hexadecimal Convesion functions 
void hexadecimal_binary(char []);
void hexadecimal_octal(char []);
void hexadecimal_decimal(char []);

// C-Program main function 
int main()
{
    welcomeScreen();
}

// Intro screen 
void welcomeScreen()
{
    int choice;

label1:
    screenCleaner();
    printf("-------------------------------------------\n");
    printf(">>> Welcome to Number System Converter <<< \n");
    printf("-------------------------------------------\n\n");

    printf(">> Select Conversion Type: \n");
    printf("> 1. Binary Conversion \n");
    printf("> 2. Decimal Conversion \n");
    printf("> 3. Octal Conversion \n");
    printf("> 4. Hexadecimal Conversion \n");
    printf("> 5. Exit the Program \n\n");
    printf("Enter the number & Hit ENTER: ");
    scanf("%d", &choice);

    // passes the user input for conversion 
    switch(choice)
    {
        case 1:
            userInput(1);
            break;
        case 2:
            userInput(2);
            break;
        case 3:
            userInput(3);
            break;
        case 4:
            userInput(4);
            break;
        case 5:
            exitScreen();
            break;
        default:
            printf("\nError: the number must be between 1 to 5.\n");
            printf("Press any key to continue... \n");
            getch();
            goto label1;
    }
}

// program exit screen (credit page) 
void exitScreen()
{
    screenCleaner();
    printf("-------------------------------------------\n");
    printf(" >>> Creator: Ganesh Mourya (@Alkaison) <<< \n");
    printf("-------------------------------------------\n\n");

    printf("> GitHub: https://github.com/Alkaison \n");
    printf("> Twitter: https://twitter.com/Alkaison \n");
    printf("> LinkedIn: https://www.linkedin.com/in/Alkaison \n\n");

    exit(0);  // exit() function to close the program safely 
}

void screenCleaner()
{
    system("cls");  // clears the output screen 
    fflush(stdin);  // clears the input buffer 
}

void userInput(int choice)
{
    screenCleaner();

    if(choice == 1) // Binary input validation code 
    {    
        long int bi;
        int flag = 0;

        printf("Enter the binary: ");
        scanf("%ld", &bi);

        flag = digitChecker(bi, choice);

        if(flag == 1)
        {
            printf("\nError: Binary can only have the digits 0, 1. \n");
            printf("Press any key to continue... \n");
            getch();
            welcomeScreen();
        }
        else
        {
            conversion_Title();
            binary_decimal(bi);
            binary_octal(bi);
            binary_hexadecimal(bi);
            tryAgain(choice);
        }
    }
    else if(choice == 2)  // Decimal input validation code 
    {
        long int deci;
        int flag = 0;

        printf("Enter the decimal: ");
        scanf("%ld", &deci);

        if(deci > 0)
            flag = digitChecker(deci, choice);
        else
            flag = 1;
        
        if(flag == 1)
        {
            printf("\nError: Decimal number can't be negative. \n");
            printf("Press any key to continue... \n");
            getch();
            welcomeScreen();
        }
        else
        {
            conversion_Title();
            decimal_binary(deci);
            decimal_octal(deci);
            decimal_hexadecimal(deci);
            tryAgain(choice);
        }
    }
    else if(choice == 3)  // Octal input validation code 
    {
        long int octal;
        int flag = 0;

        printf("Enter the octal: ");
        scanf("%ld", &octal);

        flag = digitChecker(octal, choice);
  
        if(flag == 1)
        {
            printf("\nError: Octal digits can only be between 0 to 7. \n");
            printf("Press any key to continue... \n");
            getch();
            welcomeScreen();
        }
        else
        {
            conversion_Title();
            octal_binary(octal);
            octal_decimal(octal);
            octal_hexadecimal(octal);
            tryAgain(choice);
        }
    }
    else if(choice == 4)  // HexaDecimal input validation code 
    {
        char hexa[50];
        char ch;
        int i=0, j=0, k=0, flag=0;

        printf("Enter the hexadecimal: ");

        while(1)
        {
            ch = getch();
            if(ch == ENTER || ch == TAB)
            {
                hexa[i] = '\0';
                break;
            }
            else if(ch == BKSP)
            {
                if(i > 0)
                {
                    i--;
                    printf("\b \b"); // for backspace
                }
            }
            else
            {
                hexa[i++] = ch;
                printf("%c", ch);
            }
        }   

        for(j=0; j<i; j++)
        {
            if((hexa[j] >= 'A' && hexa[j] <= 'F') || (hexa[j] >= 'a' && hexa[j] <= 'f') || isdigit(hexa[j]))
                k++;
            else
            {
                flag = 1;
                break;
            }
        }   

        if(flag == 1)
        {
            printf("\n\nError: Hexadecimal digits can only be between 0 to 9 & A to F. \n");
            printf("Press any key to continue... \n");
            getch();
            welcomeScreen();
        }
        else
        {
            printf("\n");
            conversion_Title();
            hexadecimal_binary(hexa);
            hexadecimal_octal(hexa);
            hexadecimal_decimal(hexa);
            tryAgain(choice);
        }
    }
    else  // Very rare case message 
        printf("\n>> Unexpected Error occured. Report to program Administrator << \n");
}

// validation function for each single digit of a number according to conversion condition 
int digitChecker(int num, int choice)
{
    long int rem, temp=0, flag=0;
    temp = num;

        while(temp != 0)
        {    
            rem = temp % 10;

            if((rem == 0 || rem == 1) && choice == 1) // binary, choice = 1 
                temp = temp / 10;
            else if(rem >= 0 && rem <= 9 && choice == 2) // decimal, choice = 2
                temp = temp / 10;
            else if(rem >= 0 && rem <=7 && choice == 3) // octal, choice = 3
                temp = temp / 10;
            else
            {
                flag = 1;
                break;
            }
        }
    return flag;
}

// title for all conversion outputs 
void conversion_Title()
{
    printf("\n---------------------------\n");
    printf(">>> Conversion Results <<< \n");
    printf("---------------------------\n");
}

// try Again window 
void tryAgain(int choice)
{
    char ch;

    printf("\n\nDo you want to try again [y/N]: ");
    scanf(" %c", &ch);

    switch (ch)
    {
        case 'Y':
        case 'y':
            userInput(choice);
            break;
        case 'N':
        case 'n':
            welcomeScreen();
            break;
        default:
            printf("\nError: invalid input. \n");
            printf("Press any key to continue... \n");
            getch();
            welcomeScreen();
    }
}

// Binary Conversion functions
void binary_decimal(long int bi)
{
    int rem,sum=0,i=0;

    while(bi!=0)
    {
        rem=bi%10;
        bi=bi/10;
        sum=sum+rem*pow(2,i);
        i++;
    }
    
    printf("\nDecimal Number: %d",sum);
}

void binary_octal(long int bi)
{
    int i=0,rem,sum=0,remain[100],len=0;

    while(bi!=0)
    {
        rem=bi%10;
        bi=bi/10;
        sum=sum+rem*pow(2,i);
        i++;
    }
    i=0;
    while(sum!=0)
    {
        remain[i]=sum%8;
        sum=sum/8;
        i++;
        len++;
    }

    printf("\nOctal Number: ");
    for(i=len-1;i>=0;i--)
    {
        printf("%d",remain[i]);
    }
}

void binary_hexadecimal(long int bi)
{
    int rem,i=0,sum=0,remain[100],len=0;

    while(bi!=0)
    {
        rem=bi%10;
        bi=bi/10;
        sum=sum+rem*pow(2,i);
        i++;
    }
    i=0;
    while(sum!=0)
    {
        remain[i]=sum%16;
        sum=sum/16;
        i++;
        len++;
    }

    printf("\nHexa-Decimal Number: ");
    for(i=len-1;i>=0;i--)
    {
        switch(remain[i])
        {
            case 10:
                printf("A"); 
                break;
            case 11:
                printf("B"); 
                break;
            case 12:
                printf("C"); 
                break;
            case 13:
                printf("D"); 
                break;
            case 14:
                printf("E"); 
                break;
            case 15:
                printf("F"); 
                break;
            default:
                printf("%d",remain[i]);
        }
    }
}

// Decimal Conversion functions 
void decimal_binary(long int deci)
{
    int rem[50],i,len=0;

    do
    {
        rem[i]=deci%2;
        deci=deci/2;
        i++;
        len++;
    }
    while(deci !=0);

    printf("\nBinary Number: ");
    for(i=len-1;i>=0;i--)
    {
        printf("%d",rem[i]);
    }
}

void decimal_octal(long int deci)
{
    int rem[50],i,len=0;

    do
    {
        rem[i]=deci%8;
        deci=deci/8;
        i++;
        len++;
    }
    while(deci!=0);

    printf("\nOctal Number: ");
    for(i=len-1;i>=0;i--)
    {
        printf("%d",rem[i]);
    }
}

void decimal_hexadecimal(long int deci)
{
    int rem[50],i,len=0;

    do
    {
        rem[i]=deci%16;
        deci=deci/16;
        i++;
        len++;
    }
    while(deci!=0);

    printf("\nHexa-Decimal Number: ");
    for(i=len-1;i>=0;i--)
    {
        switch(rem[i])
        {
            case 10:
                printf("A"); 
                break;
            case 11:
                printf("B"); 
                break;
            case 12:
                printf("C"); 
                break;
            case 13:
                printf("D"); 
                break;
            case 14:
                printf("E"); 
                break;
            case 15:
                printf("F"); 
                break;
            default:
                printf("%d",rem[i]);
        }
    }
}

// Octal Conversion functions 
void octal_binary(long int oct)
{
    int rem[50],len=0,decimal=0,i=0,num,ans;

    while(oct!=0)
    {
        ans=oct % 10;
        decimal = decimal + ans * pow(8,i);
        i++;
        oct = oct/10;
    }

    i=0;
    do
    {
        rem[i]=decimal%2;
        decimal=decimal/2;
        i++;
        len++;
    }
    while(decimal!=0);

    printf("\nBinary Number: ");
    for(i=len-1;i>=0;i--)
    {
        printf("%d",rem[i]);
    }
}

void octal_decimal(long int oct)
{
    int decimal=0,i=0,num,ans;

    while(oct!=0)
    {
        ans=oct % 10;
        decimal = decimal + ans * pow(8,i);
        i++;
        oct = oct/10;
    }
    printf("\nDecimal Number: %d",decimal);
}

void octal_hexadecimal(long int oct)
{
    int rem[50],len=0,decimal=0,i=0,num,ans=0;
    while(oct!=0)
    {
        ans=oct % 10;
        decimal = decimal + ans * pow(8,i);
        i++;
        oct = oct/10;
    }

    i=0;
    while(decimal!=0)
    {
        rem[i]=decimal%16;
        decimal=decimal/16;
        i++;
        len++;
    }

    printf("\nHexa-Decimal Number: ");
    
    for(i=len-1;i>=0;i--)
    {
        switch(rem[i])
        {
            case 10:
                printf("A"); 
                break;
            case 11:
                printf("B"); 
                break;
            case 12:
                printf("C"); 
                break;
            case 13:
                printf("D"); 
                break;
            case 14:
                printf("E"); 
                break;
            case 15:
                printf("F"); 
                break;
            default:
                printf("%d",rem[i]);
        }
    }
}

// Hexadecimal Convesion functions 
void hexadecimal_binary(char hexa[])
{
    int i=0;

    printf("\nBinary Number: ");

    for(i=0;i<strlen(hexa);i++)
    {
        switch (hexa[i])
        {
            case '0':
                printf("0000"); 
                break;
            case '1':
                printf("0001"); 
                break;
            case '2':
                printf("0010"); 
                break;
            case '3':
                printf("0011"); 
                break;
            case '4':
                printf("0100"); 
                break;
            case '5':
                printf("0101"); 
                break;
            case '6':
                printf("0110"); 
                break;
            case '7':
                printf("0111"); 
                break;
            case '8':
                printf("1000"); 
                break;
            case '9':
                printf("1001"); 
                break;
            case 'A':
            case 'a':
                printf("1010"); 
                break;
            case 'B':
            case 'b':
                printf("1011"); 
                break;
            case 'C':
            case 'c':
                printf("1100"); 
                break;
            case 'D':
            case 'd':
                printf("1101"); 
                break;
            case 'E':
            case 'e':
                printf("1110"); 
                break;
            case 'F':
            case 'f':
                printf("1111"); 
                break;
            default:
                printf("\n Invalid hexa digit %c ", hexa[i]);
        }
    }
}

void hexadecimal_octal(char hexa[])
{
    int i,len,num=0,power=0,decimal=0,rem[100];

    for(i=strlen(hexa)-1;i>=0;i--)
    {
        if(hexa[i]=='A'||hexa[i]=='a')
            num=10;
        else if(hexa[i]=='B'||hexa[i]=='b')
            num=11;
        else if(hexa[i]=='C'||hexa[i]=='c')
            num=12;
        else if(hexa[i]=='D'||hexa[i]=='d')
            num=13;
        else if(hexa[i]=='E'||hexa[i]=='e')
            num=14;
        else if(hexa[i]=='F'||hexa[i]=='f')
            num=15;
        else
            num=hexa[i]-48;

        decimal=decimal+num*pow(16,power);
        power++;
    }

    i=0,len=0;
    while(decimal!=0)
    {
        rem[i]=decimal%8;
        decimal=decimal/8;
        i++;
        len++;
    }

    printf("\nOctal Number: ");
    for(i=len-1;i>=0;i--)
    {
        printf("%d",rem[i]);
    }
}

void hexadecimal_decimal(char hexa[])
{
    int i,num=0,power=0,decimal=0;

    for(i=strlen(hexa)-1;i>=0;i--)
    {
        if(hexa[i]=='A'||hexa[i]=='a')
            num=10;
        else if(hexa[i]=='B'||hexa[i]=='b')
            num=11;
        else if(hexa[i]=='C'||hexa[i]=='c')
            num=12;
        else if(hexa[i]=='D'||hexa[i]=='d')
            num=13;
        else if(hexa[i]=='E'||hexa[i]=='e')
            num=14;
        else if(hexa[i]=='F'||hexa[i]=='f')
            num=15;
        else
            num=hexa[i]-48;

        decimal=decimal+num*pow(16,power);
        power++;
    }
    printf("\nDecimal Number: %d",decimal);
}
