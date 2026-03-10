#include <stdio.h>
#include <string.h>

int main()
{
    int n,i,time=0,completed=0;
    char pid[20][10];
    int at[20],bt[20],pr[20];
    int wt[20],tat[20],ct[20];
    int done[20]={0};
    float avg_wt=0,avg_tat=0;

    scanf("%d",&n);

    for(i=0;i<n;i++)
    {
        scanf("%s %d %d %d",pid[i],&at[i],&bt[i],&pr[i]);
    }

    while(completed<n)
    {
        int idx=-1;
        int min_pr=9999;

        for(i=0;i<n;i++)
        {
            if(at[i]<=time && done[i]==0)
            {
                if(pr[i]<min_pr)
                {
                    min_pr=pr[i];
                    idx=i;
                }
            }
        }

        if(idx!=-1)
        {
            time+=bt[idx];
            ct[idx]=time;
            tat[idx]=ct[idx]-at[idx];
            wt[idx]=tat[idx]-bt[idx];

            avg_wt+=wt[idx];
            avg_tat+=tat[idx];

            done[idx]=1;
            completed++;
        }
        else
        {
            time++;
        }
    }

    printf("Waiting Time:\n");
    for(i=0;i<n;i++)
    {
        printf("%s %d\n",pid[i],wt[i]);
    }

    printf("Turnaround Time:\n");
    for(i=0;i<n;i++)
    {
        printf("%s %d\n",pid[i],tat[i]);
    }

    avg_wt/=n;
    avg_tat/=n;

    printf("Average Waiting Time: %.2f\n",avg_wt);
    printf("Average Turnaround Time: %.2f\n",avg_tat);

    return 0;
}# OS
