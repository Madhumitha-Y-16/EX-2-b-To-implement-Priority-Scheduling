# EX-2-b-To-implement-Priority-Scheduling

## AIM
To implement the Priority CPU Scheduling Algorithm and calculate the Waiting Time and Turnaround Time for each process.

## ALGORITHM
1. Start the program.
2. Read the number of processes.
3. Enter the burst time and priority for each process.
4. Arrange the processes according to their priority.
5. The process with the highest priority is executed first.
6. Set the waiting time of the first process to 0.
7. Calculate the waiting time for the remaining processes.
8. Calculate the turnaround time using: Turnaround Time = Waiting Time + Burst Time
9. Calculate the average waiting time and average turnaround time.
10. Display the process details.
11. Stop the program.

## PROGRAM
```
#include <stdio.h>
int main()
{
    int n, i, j;
    int bt[20], priority[20], wt[20], tat[20], p[20];
    int temp;
    float avg_wt = 0, avg_tat = 0;
    printf("Enter the number of processes: ");
    scanf("%d", &n);
    printf("Enter burst time and priority for each process:\n");
    for(i = 0; i < n; i++)
    {
        p[i] = i + 1;
        printf("P%d Burst Time: ", i + 1);
        scanf("%d", &bt[i]);
        printf("P%d Priority: ", i + 1);
        scanf("%d", &priority[i]);
    }
    for(i = 0; i < n - 1; i++)
    {
        for(j = i + 1; j < n; j++)
        {
            if(priority[i] > priority[j])
            {
                temp = priority[i];
                priority[i] = priority[j];
                priority[j] = temp;

                temp = bt[i];
                bt[i] = bt[j];
                bt[j] = temp;

                temp = p[i];
                p[i] = p[j];
                p[j] = temp;
            }
        }
    }
    wt[0] = 0;
    for(i = 1; i < n; i++)
    {
        wt[i] = wt[i - 1] + bt[i - 1];
    }
    for(i = 0; i < n; i++)
    {
        tat[i] = wt[i] + bt[i];
        avg_wt += wt[i];
        avg_tat += tat[i];
    }
    avg_wt = avg_wt / n;
    avg_tat = avg_tat / n;
    printf("\nProcess\tBurst Time\tPriority\tWaiting Time\tTurnaround Time\n");
    for(i = 0; i < n; i++)
    {
        printf("P%d\t%d\t\t%d\t\t%d\t\t%d\n", p[i], bt[i], priority[i], wt[i], tat[i]);
    }

    printf("\nAverage Waiting Time = %.2f", avg_wt);
    printf("\nAverage Turnaround Time = %.2f\n", avg_tat);
    return 0;
}
```

## OUTPUT:
<img width="888" height="551" alt="{A01E17CA-8B2E-4430-A54E-D2D7CAA549A0}" src="https://github.com/user-attachments/assets/7003419e-4859-4c0b-8956-253f24f6426a" />

## RESULT:
Thus the Priority CPU Scheduling Algorithm was successfully implemented, and the waiting time, turnaround time, average waiting time, and average turnaround time were calculated.
