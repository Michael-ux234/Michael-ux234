#include <stdio.h>
#include <string.h>
#include <stdbool.h>
#include <ctype.h>
#include <stdlib.h>
#include <time.h>

bool CheckNumber(char StringNumber[]);
bool CheckDate(char CheckYear[],char CheckMonth[], char CheckDay[]);
void CurrentDay();
void StopExecutionTop();

int main()
{
    system("COLOR 4");
    char loan_applicant_CompleteName[100];
    char loan_applicant_Age[100];
    char loan_applicant_Address[100];
    char loan_applicant_RepaymentDates[100];
    char loan_applicant_LoanAmount[100];
    char loan_applicant_Payment[100];
    char repayment_year[100];
    char repayment_month[100];
    char repayment_day[100];

    float InterestRate = 0.05;
    float TotalPayment;
    float Change;
    float PaymentCheck;
    printf("\t\t\t\t\t      ::::::::::::::::::::::::::\n");
    printf("\t\t\t\t\t      ::   LOAN TRACKER SYSTEM ::\n");
    printf("\t\t\t\t\t      ::::::::::::::::::::::::::\n\n\n");
    printf("\t\t\t\t\t      [[[[[[[[[[[[[[[                                                                               ]]]]]]]]]]]]]]]\n");
    printf("\t\t\t\t\t      [::::::::::::::                                                                               ::::::::::::::]\n");
    printf("\t\t\t\t\t      [::::::::::::::                                                                               ::::::::::::::]\n");
    printf("\t\t\t\t\t      [::::::[[[[[[[:                                                                               :]]]]]]]::::::]\n");
    printf("\t\t\t\t\t      [:::::[                                                                                               ]:::::]\n");
    printf("\t\t\t\t\t      [:::::[                                                                                               ]:::::]\n");
    printf("\t\t\t\t\t      [:::::[                                                                                               ]:::::]\n");
    printf("\t\t\t\t\t      [:::::[                                                                                               ]:::::]\n");
    printf("\t\t\t\t\t      [:::::[                     Correctly fill up the following question!                                 ]:::::]\n");
    printf("\t\t\t\t\t      [:::::[                                                                                               ]:::::]\n");
    printf("\t\t\t\t\t      [:::::[     Incomplete information will prompt the program to request the necessary details again.    ]:::::]\n");
    printf("\t\t\t\t\t      [:::::[                                                                                               ]:::::]\n");
    printf("\t\t\t\t\t      [:::::[                                                                                               ]:::::]\n");
    printf("\t\t\t\t\t      [:::::[                                                                                               ]:::::]\n");
    printf("\t\t\t\t\t      [:::::[                                                                                               ]:::::]\n");
    printf("\t\t\t\t\t      [:::::[                                                                                               ]:::::]\n");
    printf("\t\t\t\t\t      [:::::[                                                                                               ]:::::]\n");
    printf("\t\t\t\t\t      [::::::[[[[[[[:                                                                               :]]]]]]]::::::]\n");
    printf("\t\t\t\t\t      [::::::::::::::                                                                               ::::::::::::::]\n");
    printf("\t\t\t\t\t      [::::::::::::::                                                                               ::::::::::::::]\n");
    printf("\t\t\t\t\t      [[[[[[[[[[[[[[[                                                                               ]]]]]]]]]]]]]]]\n");

    do
    {
        printf("\t\t\t\t\t      Complete name: ");
        fgets(loan_applicant_CompleteName, 100, stdin);
        loan_applicant_CompleteName[strlen(loan_applicant_CompleteName) - 1] = '\0';

        printf("\t\t\t\t\t      Age: ");
        fgets(loan_applicant_Age, 100, stdin);
        loan_applicant_Age[strlen(loan_applicant_Age) - 1] = '\0';

        printf("\t\t\t\t\t      Address: ");
        fgets(loan_applicant_Address, 100, stdin);
        loan_applicant_Address[strlen(loan_applicant_Address) - 1] = '\0';

        if(!CheckNumber(loan_applicant_Age))
        {
            printf("Invalid age input. Re - attempt fill up.");
        }

        if(loan_applicant_CompleteName[0] == '\0' || loan_applicant_Age[0] == '\0' || loan_applicant_Address[0] == '\0' || !CheckNumber(loan_applicant_Age))
        {
            printf("\t\t\t\t\t      Incomplete Information. Please correctly provide all required details to proceed to the next step.\n\n");
        }
        else
        {
            printf("\t\t\t\t\t      Information complete. Thank you for taking the time to provide the necessary details.\n\n");
        }

    } while (loan_applicant_CompleteName[0] == '\0' || loan_applicant_Age[0] == '\0' || loan_applicant_Address[0] == '\0' || !CheckNumber(loan_applicant_Age));

    do
    {
        printf("\t\t\t\t\t      Loan amount: ");
        fgets(loan_applicant_LoanAmount, 100, stdin);
        loan_applicant_LoanAmount[strlen(loan_applicant_LoanAmount) - 1] = '\0';

        if(!CheckNumber(loan_applicant_LoanAmount))
        {
            printf("\t\t\t\t\t      Please number only when inputting a amount. Thank you.\n");
        }

    } while (!CheckNumber(loan_applicant_LoanAmount));


    do
    {
        printf("\t\t\t\t\t      Enter repayment dates (dd/mm/yyyy)\n");
        printf("\t\t\t\t\t      Year: ");
        fgets(repayment_year, 100, stdin);
        repayment_year[strlen(repayment_year) - 1] = '\0';

        printf("\t\t\t\t\t      Month: ");
        fgets(repayment_month, 100, stdin);
        repayment_month[strlen(repayment_month) - 1] = '\0';

        printf("\t\t\t\t\t      Day: ");
        fgets(repayment_day, 100, stdin);
        repayment_day[strlen(repayment_day) - 1] = '\0';

        if(!CheckNumber(repayment_year) || !CheckNumber(repayment_month) || !CheckNumber(repayment_day))
        {
            printf("\t\t\t\t\t      Invalid Date being provided, Try Again!\n");
        }
        else
        {
            if(!CheckDate(repayment_year, repayment_month, repayment_day))
            {
                printf("\t\t\t\t\t      Invalid Date Format!\n");
            }
            else
            {
                printf("\t\t\t\t\t      Correct Format being\n");
            }
        }
    } while (!CheckNumber(repayment_year) || !CheckNumber(repayment_month) || !CheckNumber(repayment_day) || !CheckDate(repayment_year, repayment_month, repayment_day));

    InterestRate = InterestRate * atoi(loan_applicant_LoanAmount);
    TotalPayment = atoi(loan_applicant_LoanAmount) + InterestRate;

    printf("\t\t\t\t\t      ::+::::::::::::::::::::::::::::::::::::::::::::::::::+\n");
    printf("\t\t\t\t\t      ::            LOAN APPLICANT INFORMATION            |\n");
    printf("\t\t\t\t\t      :::::::::::::::::::::::::::::::::::::::::::::::::::::+\n");
    printf("\t\t\t\t\t      ::Name: %s\n", loan_applicant_CompleteName);
    printf("\t\t\t\t\t      ::Age: %s\n", loan_applicant_Age);
    printf("\t\t\t\t\t      ::Address: %s\n", loan_applicant_Address);
    printf("\t\t\t\t\t      ::Loan Amount: %s\n", loan_applicant_LoanAmount);
    printf("\t\t\t\t\t      ::Interest Rate: 5%%\n");
    printf("\t\t\t\t\t      ::Interest Amount: %.2f\n", InterestRate);
    printf("\t\t\t\t\t      ::Total Payment Loan: %.2f\n", TotalPayment);
    printf("\t\t\t\t\t      ::Dated Loan: ");
    CurrentDay();
    printf("\n\t\t\t\t\t      ::Promise will be paid on: %s-%s-%s", repayment_month, repayment_day, repayment_year);
    printf("\n\t\t\t\t\t      ::+--------------------------------------------------+\n");

    StopExecutionTop();

    do
    {
        printf("\n\t\t\t\t\t      Enter your payment: ");
        fgets(loan_applicant_Payment, 100, stdin);
        loan_applicant_Payment[strlen(loan_applicant_Payment) - 1] = '\0';

        if(!CheckNumber(loan_applicant_Payment))
        {
            printf("\t\t\t\t\t      Please! you must only input number.");
        }
        else
        {
            Change = atof(loan_applicant_Payment);
            PaymentCheck = Change - TotalPayment;
            if(PaymentCheck < 0)
            {
                printf("\t\t\t\t\t      Insufficient balance. Try again!\n");
            }
            else
            {
                printf("\t\t\t\t\t      Payment is received!\n");
                printf("\t\t\t\t\t      Change: %.2f\n", PaymentCheck);
                printf("\t\t\t\t\t      Thank you!");
                return 0;
            }
        }

    }while(!CheckNumber(loan_applicant_Payment) || PaymentCheck < 0);

    return 0;
}

bool CheckNumber(char StringNumber[])
{
    for(int i = 0;  i < strlen(StringNumber); i++)
    {
        if(!isdigit(StringNumber[i]))
        {
            return false;
        }
    }
    return true;
}

bool CheckDate(char CheckYear[],char CheckMonth[], char CheckDay[])
{
    time_t now = time(NULL);
    struct tm *CurrentTime = localtime(&now);

    int userYearInput = atoi(CheckYear);
    int userMonthInput = atoi(CheckMonth);
    int userDayInput = atoi(CheckDay);

    int currentYear;
    int currentMonth;
    int currentDay;

    currentYear = CurrentTime -> tm_year;
    currentYear = currentYear + 1900;

    currentMonth = CurrentTime -> tm_mon;
    currentMonth = currentMonth + 1;

    currentDay = CurrentTime -> tm_mday;

    if(currentYear > userYearInput) return false;
    if(currentYear == userYearInput && currentMonth > userMonthInput) return false;
    if(userMonthInput > 12) return false;
    if(currentYear == userYearInput && currentMonth == userMonthInput && currentDay > userDayInput) return false;
    if (userDayInput > 31) return false;


    return true;
}

void CurrentDay()
{
    time_t now = time(NULL);
    struct tm *CurrentTime = localtime(&now);

    int currentYear = CurrentTime -> tm_year;
    int currentMonth = CurrentTime -> tm_mon;
    int currentDay = CurrentTime -> tm_mday;
    printf("%d/%d/%d", currentMonth + 1, currentDay, currentYear + 1900);
}

void StopExecutionTop()
{
    struct timespec SleepSeconds, TimeRemain = {3, 100};
    nanosleep(&TimeRemain, &SleepSeconds);
}
