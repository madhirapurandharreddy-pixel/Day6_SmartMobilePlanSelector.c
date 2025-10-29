#include <stdio.h>

int main()
{
    float dataUsed, baseCost = 0, extraData = 0, totalBill = 0, finalBill = 0;
    int student, corporate;
    float discount = 0;
    char plan[20];

    printf("Enter total data used (GB): ");
    scanf("%f", &dataUsed);

    printf("Are you a student? (1-Yes / 0-No): ");
    scanf("%d", &student);

    printf("Corporate user? (1-Yes / 0-No): ");
    scanf("%d", &corporate);

    if (dataUsed > 100)
    {
        printf("\nExcessive Usage – Plan Not Allowed\n");
    }
    else
    {

        if (dataUsed < 30)
        {
            baseCost = 299;
            extraData = 0;
            totalBill = baseCost;
            sprintf(plan, "Silver");
        }
        else if (dataUsed >= 30 && dataUsed <= 60)
        {
            baseCost = 499;
            if (dataUsed > 60)
                extraData = dataUsed - 60;
            else
                extraData = 0;
            totalBill = baseCost + (extraData * 40);
            sprintf(plan, "Gold");
        }
        else if (dataUsed > 60)
        {
            baseCost = 799;
            if (dataUsed > 60)
                extraData = dataUsed - 60;
            else
                extraData = 0;
            totalBill = baseCost + (extraData * 30);
            sprintf(plan, "Platinum");
        }


        if (student == 1 && corporate == 1)
        {

            discount = 15;
        }
        else if (student == 1)
        {
            discount = 15;
        }
        else if (corporate == 1)
        {
            discount = 10;
        }
        else
        {
            discount = 0;
        }

        finalBill = totalBill - (totalBill * discount / 100);

        printf("\nUser Plan Summary:\n");
        printf("Data Used: %.0f GB\n", dataUsed);
        printf("Selected Plan: %s\n", plan);
        printf("Base Cost: ₹%.2f\n", baseCost);
        printf("Extra Data: %.0f GB\n", extraData);
        if (extraData > 0)
            printf("Total (before discount): ₹%.2f\n", totalBill);
        printf("Discount Applied: %.0f%%\n", discount);
        printf("Final Bill: ₹%.2f\n", finalBill);
    }

    return 0;
}
