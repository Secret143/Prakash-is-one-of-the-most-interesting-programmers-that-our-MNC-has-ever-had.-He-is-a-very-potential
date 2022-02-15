#include<math.h>
#include<stdio.h>
#include<conio.h>
#include<stdlib.h>
 
int arr[5][5];
int sol[30];
int k = 1,countnumber[25];
int flag = 1;
int printRepeating(int arr[], int size)
{
    int i;
    for (i = 0; i < size; i++)
{
if (arr[abs(arr[i])] >= 0)
        {
            arr[abs(arr[i])] = -arr[abs(arr[i])];
    }
    else
        {
            // printf("\nNO TREASURE");
            flag = flag * 0;
            break;
        }
    }
}
 
int search(int a[][5], int x, int y)
{
int count = 0,tempx = 0,tempy = 0,p,c = 1;
int tempcondition,i,flag = 1;
 
    while (a[x][y] != tempcondition)
    {
        tempcondition = (((x + 1) * 10) + (y + 1));
        if (x == 0 && y == 0)
        {
            sol[0] = (x + 1) * 10 + (y + 1);
            // printf("%d %d",x+1,y+1);
            // ++count;
        }
        if (a[x][y] != tempcondition)
        {
            if (c < 25)
            {
                sol[c] = a[x][y];
            }
            else
            {
                p = printRepeating(sol, 30);
                if (p == 0)
                {
                    flag = 0;
                    break;
                }
 
            }
 
            tempx = a[x][y] / 10;
            tempy = a[x][y] % 10;
            x = tempx - 1;
            y = tempy - 1;
            // printf("\n%d %d",x+1,y+1);
            c++;
            count++;
 
        }
 
    }
    if (flag == 1)
    {
        for (i = 0; i <= count; i++)
        {
            tempx = sol[i] / 10;
            tempy = sol[i] % 10;
            printf("%d %d\n", tempx, tempy);
        }
    }
    else
    printf("NO TREASURE");
 
}
 
int main()
{
 
int i,j,checkflag = 0;
    for (i = 0; i < 5; i++)
    {
        for (j = 0; j < 5; j++)
        {
            scanf("%d", &arr[i][j]);
        }
    }
    for (i = 0; i < 5; i++)
    {
     for (j = 0; j < 5; j++)      
{        
   if ((arr[i][j] / 10) >= 1 && (arr[i][j] / 10) <= 5 &&          (arr[i][j] % 10) >= 1 && (arr[i][j] / 10) <= 5)
            {
            checkflag = 1;
 
            }
            else
            {
                checkflag = 0;
                break;
 
            }
        }
    }
    if (checkflag == 0)
    {
        printf("NO TREASURE");
    }
    else
    {
        search(arr, 0, 0);
    }
}
