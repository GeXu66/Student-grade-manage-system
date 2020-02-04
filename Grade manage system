    #include<stdio.h>
    #include<string.h>
    #include<stdlib.h>
    #define StudentMax 30
    #define CourseMax 6
    #define Group 5
    typedef struct student
    {
        long studentID;
        char studentName[12];
        int score[6];
    }STUDENT;
    void Read(STUDENT stu[],float avers[],float averc[],int sums[],int sumc[],int n,int k,char course[][12]);
    void Avers(STUDENT stu[],int sums[],float avers[],int n,int k);
    void Averc(STUDENT stu[],int sumc[],float averc[],int n,int k);
    void Selectionsortbysums(STUDENT stu[],int n,int k,int sums[],int (*compare)(int a,int b),char course[][12]);
    int Ascending(int a,int b);
    int Decending(int a,int b);
    void swap(int *a,int *b);
    void AscendingID(STUDENT stu[],int n,int k,int (*compare)(int a,int b),char course[][12],int sums[]);
    void Sortbystring(STUDENT stu[],int n,int k,char course[][12],int sums[]);
    void SearchbyID(STUDENT stu[],int n,int k,int (*compare)(int a,int b),char course[][12],int sums[]);
    void Searchbyname(STUDENT stu[],int n,int k,char course[][12],int sums[],int (*compare)(int a,int b));
    void Setgroup(STUDENT stu[],int n,int k,char course[][12],int group[][5]);
    void Printall(STUDENT stu[],int n,int k,char course[][12],int sums[],float avers[]);
    void Writetofile(STUDENT stu[],int n,int k);
    int Readfromfile(STUDENT stu[],int n,int k);
    int main()
    {
        system("color f0");
        printf("Number:190320517\n");
        printf("Program_9\n");
        int r,n,k,i,j,m,choice,flag=0;
        char answer[30];
        STUDENT stu[StudentMax];
        int sums[StudentMax]={-1},sumc[CourseMax]={-1};
        float avers[StudentMax]={-1},averc[CourseMax]={-1};
        int group[CourseMax][Group]={0};
        char course[CourseMax][12];
        do
        {
            printf("please input the number of the student\n");
            r=0;
            r=scanf("%d",&n);
            if(r==0)
            {
                printf("error!there is a problem in your input!\n");
                fflush(stdin);
                continue;
            }
            else if(n>30||n<=0)
            {
                printf("error!the number of student is over 30!please input again!\n");
                fflush(stdin);
                continue;
            }
            else
            {
                fflush(stdin);
                break;
            }
        }
        while(1);
        do
        {
            printf("please input the number of the subject\n");
            r=0;
            r=scanf("%d",&k);
            if(r==0)
            {
                printf("error!there is a problem in your input!\n");
                fflush(stdin);
                continue;
            }
            else if(k<=0||k>6)
            {
                printf("error!the number of course is over 6!please input again!\n");
                fflush(stdin);
                continue;
            }
            else
            {
                fflush(stdin);
                break;
            }
        }
        while(1);
        do
        {
            r=0;
            for(j=0;j<k;j++)
            {
                printf("please input the name of the course\n");
                fgets(course[j],12,stdin);
                course[j][strlen(course[j])-1]='\0';
            }
            printf("please confirm your input:");
            for(i=0;i<k;i++)
            {
                printf("%s\t",course[i]);
            }
            printf("\nplease input t/T to continue or f/F to input again:");
            r=scanf(" %s",answer);
            if(r==0)
            {
                printf("input error!please input the course name again!\n");
                fflush(stdin);
                continue;
            }
            else if(strlen(answer)>1)
            {
                printf("input error!please input the course name again!\n");
                fflush(stdin);
                continue;
            }
            else if(answer[0]=='t'||answer[0]=='T')
            {
                getchar();
                break;
            }
            else if(answer[0]=='f'||answer[0]=='F')
            {
                getchar();
                printf("you can input again!\n");
                continue;
            }
            else
            {
                printf("error!please input the course name again!\n");
                fflush(stdin);
                continue;
            }
        }
        while(1);
        for(i=0;;i++)
        {
            printf("\n1.Input record\n");
            printf("2.Calculate total and average score of every course\n");
            printf("3.Calculate total and average score of every student\n");
            printf("4.Sort in descending order by total score of every student\n");
            printf("5.Sort in ascending order by total score of every student\n");
            printf("6.Sort in ascending order by number\n");
            printf("7.Sort in dictionary order by name\n");
            printf("8.Search by number\n");
            printf("9.Search by name\n");
            printf("10.Statistic analysis for every course\n");
            printf("11.List record\n");
            printf("12.Write to a file\n");
            printf("13.Read from a file\n");
            printf("0.Exit\n");
            printf("please input your choice\n");
            scanf("%d",&choice);
            if(choice==0)
            {
                return 0;
            }
            else if(choice==1)
            {
                flag=1;
                Read(stu,avers,averc,sums,sumc,n,k,course);
            }
            else if(choice==2)
            {
                if(flag==0)
                {
                    printf("error!please input data first!\n");
                    continue;
                }
                if(sumc[0]==-1)
                {
                    Averc(stu,sumc,averc,n,k);
                }
                for(m=0;m<k;m++)
                {
                    printf("the total score of %s is %d\n",course[m],sumc[m]);
                    printf("the average score of %s is %lf\n",course[m],averc[m]);
                }
            }
            else if(choice==3)
            {
                if(flag==0)
                {
                    printf("error!please input data first!\n");
                    continue;
                }
                if(sums[0]==-1)
                {
                    Avers(stu,sums,avers,n,k);
                }
                for(m=0;m<n;m++)
                {
                    printf("the total score of %s is %d\n",stu[m].studentName,sums[m]);
                    printf("the average score of %s is %lf\n",stu[m].studentName,avers[m]);
                }
            }
            else if(choice==4)
            {
                if(flag==0)
                {
                    printf("error!please input data first!\n");
                    continue;
                }
                Selectionsortbysums(stu,n,k,sums,Decending,course);
            }
            else if(choice==5)
            {
                if(flag==0)
                {
                    printf("error!please input data first!\n");
                    continue;
                }
                Selectionsortbysums(stu,n,k,sums,Ascending,course);
            }
            else if(choice==6)
            {
                if(flag==0)
                {
                    printf("error!please input data first!\n");
                    continue;
                }
                AscendingID(stu,n,k,Ascending,course,sums);
            }
            else if(choice==7)
            {
                if(flag==0)
                {
                    printf("error!please input data first!\n");
                    continue;
                }
                Sortbystring(stu,n,k,course,sums);
            }
            else if(choice==8)
            {
                if(flag==0)
                {
                    printf("error!please input data first!\n");
                    continue;
                }
                SearchbyID(stu,n,k,Decending,course,sums);
            }
            else if(choice==9)
            {
                if(flag==0)
                {
                    printf("error!please input data first!\n");
                    continue;
                }
                Searchbyname(stu,n,k,course,sums,Decending);
            }
            else if(choice==10)
            {
                if(flag==0)
                {
                    printf("error!please input data first!\n");
                    continue;
                }
                Setgroup(stu,n,k,course,group);
            }
            else if(choice==11)
            {
                if(flag==0)
                {
                    printf("error!please input data first!\n");
                    continue;
                }
                Printall(stu,n,k,course,sums,avers);
            }
            else if(choice==12)
            {
                if(flag==0)
                {
                    printf("error!please input data first!\n");
                    continue;
                }
                Writetofile(stu,n,k);
            }
            else if(choice==13)
            {
                Readfromfile(stu,n,k);
            }
            else
            {
                printf("input error!please input again!\n");
            }
        }
    }
    //输入学生数据并计算总分与平均分
    void Read(STUDENT stu[],float avers[],float averc[],int sums[],int sumc[],int n,int k,char course[][12])
    {
            int i,j,r;
            char answer1[30];
            INPUTAGAIN:
            for(i=0;i<n;i++)
            {
                do
                {
                    r=0;
                    printf("please input the ID of the student:");
                    r=scanf("%ld",&stu[i].studentID);
                    if(r==0)
                    {
                        printf("input error!please input again!\n");
                        fflush(stdin);
                        continue;
                    }
                    else
                    {
                        fflush(stdin);
                        break;
                    }
                }
                while(1);
                printf("please input the name of the student:");
                gets(stu[i].studentName);
                for(j=0;j<k;j++)
                {
                    do
                    {
                        r=0;
                        printf("please input the score of %s:",course[j]);
                        r=scanf("%d",&stu[i].score[j]);
                        if(r==0)
                        {
                            printf("input error!please input again!\n");
                            fflush(stdin);
                            continue;
                        }
                        else if(stu[i].score[j]<0||stu[i].score[j]>100)
                        {
                            printf("error!the score of this course is illegal!\n");
                            fflush(stdin);
                            continue;
                        }
                        else
                        {
                            fflush(stdin);
                            break;
                        }
                    }
                    while(1);
                }
            }
            printf("please confirm your input.\n");
            printf("studentID\tstudentName\t");
            for(i=0;i<k;i++)
            {
                printf("%10s\t",course[i]);
            }
            for(i=0;i<n;i++)
            {
                printf("\n%10ld%10s",stu[i].studentID,stu[i].studentName);
                for(j=0;j<k;j++)
                {
                    printf("%18d",stu[i].score[j]);
                }
            }
            do
            {
                printf("\nif there is no problem,please input t/T to continue or input f/F to input again.\n");
                r=0;
                r=scanf(" %s",answer1);
                if(r==0)
                {
                    printf("error!there is a problem in your input!\n");
                    fflush(stdin);
                    continue;
                }
                else if(strlen(answer1)>1)
                {
                    printf("error!there is a problem in your input!\n");
                    fflush(stdin);
                    continue;
                }
                else if(answer1[0]=='t'||answer1[0]=='T')
                {
                    break;
                }
                else if(answer1[0]=='f'||answer1[0]=='F')
                {
                    goto INPUTAGAIN;
                }
                else
                {
                    printf("error!there is a problem in your input!\n");
                    fflush(stdin);
                    continue;
                }
            }
            while(1);
            getchar();
            Avers(stu,sums,avers,n,k);
            Averc(stu,sumc,averc,n,k);
    }
    //计算学生总分与平均分
    void Avers(STUDENT stu[],int sums[],float avers[],int n,int k)
    {
        int i,j;
        for(i=0;i<n;i++)
        {
            sums[i]=0;
            for(j=0;j<k;j++)
            {
                sums[i]=sums[i]+stu[i].score[j];
            }
        }
        for(i=0;i<n;i++)
        {
            avers[i]=(float)sums[i]/k;
        }
    }
    //计算每门课程的总分与平均分
    void Averc(STUDENT stu[],int sumc[],float averc[],int n,int k)
    {
        int i,j;
        for(j=0;j<k;j++)
        {
            sumc[j]=0;
            for(i=0;i<n;i++)
            {
                sumc[j]=sumc[j]+stu[i].score[j];
            }
        }
        for(i=0;i<k;i++)
        {
            averc[i]=(float)sumc[i]/n;
        }
    }
    //对成绩进行升序或降序排列
    void Selectionsortbysums(STUDENT stu[],int n,int k,int sums[],int (*compare)(int a,int b),char course[][12])
    {
        int i,j,m;
        STUDENT temp;
        for(i=0;i<n-1;i++)
        {
            m=i;
            for(j=i+1;j<n;j++)
            {
                if((*compare)(sums[j],sums[m]))
                {
                    m=j;
                }
            }
            if(m!=i)
            {
                temp=stu[i];
                stu[i]=stu[m];
                stu[m]=temp;
                swap(&sums[i],&sums[m]);
            }
        }
            printf("studentID\tstudentName\t");
            for(i=0;i<k;i++)
            {
                printf("%10s\t",course[i]);
            }
            for(i=0;i<n;i++)
            {
                printf("\n%10ld%10s",stu[i].studentID,stu[i].studentName);
                for(j=0;j<k;j++)
                {
                    printf("%18d",stu[i].score[j]);
                }
            }
    }
    //升序
    int Ascending(int a,int b)
    {
        return a<b;
    }
    //降序
    int Decending(int a,int b)
    {
        return a>b;
    }
    //用指针交换两个数
    void swap(int *a,int *b)
    {
        int temp;
        temp=*a;
        *a=*b;
        *b=temp;
    }
    //按照学号升序来排列
    void AscendingID(STUDENT stu[],int n,int k,int (*compare)(int a,int b),char course[][12],int sums[])
    {
        int i,j,m;
        STUDENT temp;
        for(i=0;i<n-1;i++)
        {
            m=i;
            for(j=i+1;j<n;j++)
            {
                if((*compare)(stu[j].studentID,stu[m].studentID))
                {
                    m=j;
                }
            }
            if(m!=i)
            {
                temp=stu[i];
                stu[i]=stu[m];
                stu[m]=temp;
                swap(&sums[i],&sums[m]);
            }
        }
            printf("studentID\tstudentName\t");
            for(i=0;i<k;i++)
            {
                printf("%10s\t",course[i]);
            }
            for(i=0;i<n;i++)
            {
                printf("\n%10ld%10s",stu[i].studentID,stu[i].studentName);
                for(j=0;j<k;j++)
                {
                    printf("%18d",stu[i].score[j]);
                }
            }
    }
    //按字母在字典中的顺序排列
    void Sortbystring(STUDENT stu[],int n,int k,char course[][12],int sums[])
    {
        int i,j;
        STUDENT temp;
        for(i=0;i<n-1;i++)
        {
            for(j=i+1;j<n;j++)
            {
                if(strcmp(stu[i].studentName,stu[j].studentName)>0)
                {
                    temp=stu[i];
                    stu[i]=stu[j];
                    stu[j]=temp;
                    swap(&sums[i],&sums[j]);
                }
            }
        }
            printf("studentID\tstudentName\t");
            for(i=0;i<k;i++)
            {
                printf("%10s\t",course[i]);
            }
            for(i=0;i<n;i++)
            {
                printf("\n%10ld%10s",stu[i].studentID,stu[i].studentName);
                for(j=0;j<k;j++)
                {
                    printf("%18d",stu[i].score[j]);
                }
            }
    }
    //按照学号搜索
    void SearchbyID(STUDENT stu[],int n,int k,int (*compare)(int a,int b),char course[][12],int sums[])
    {
        int i,j,m;
        long key;
        int flag=0;
        STUDENT temp;
        for(i=0;i<n-1;i++)
        {
            m=i;
            for(j=i+1;j<n;j++)
            {
                if((*compare)(sums[j],sums[m]))
                {
                    m=j;
                }
            }
            if(m!=i)
            {
                temp=stu[i];
                stu[i]=stu[m];
                stu[m]=temp;
                swap(&sums[i],&sums[m]);
            }
        }
        printf("please input the ID you want:");
        scanf("%ld",&key);
        getchar();
        for(i=0;i<n;i++)
        {
            if(key==stu[i].studentID)
            {
                flag=1;
                printf("his/her name is %s,his/her rank is %d\n",stu[i].studentName,i+1);
                for(j=0;j<k;j++)
                {
                    printf("the score of %s is %d\n",course[j],stu[i].score[j]);
                }
            }
        }
        if(flag==0)
        {
            printf("error!not find!");
            fflush(stdin);
        }
    }
    //按照名字搜索
    void Searchbyname(STUDENT stu[],int n,int k,char course[][12],int sums[],int (*compare)(int a,int b))
    {
        int i,j,m;
        char key[12];
        STUDENT temp;
        char *flag="GG";
        for(i=0;i<n-1;i++)
        {
            m=i;
            for(j=i+1;j<n;j++)
            {
                if((*compare)(sums[j],sums[m]))
                {
                    m=j;
                }
            }
            if(m!=i)
            {
                temp=stu[i];
                stu[i]=stu[m];
                stu[m]=temp;
                swap(&sums[i],&sums[m]);
            }
        }
        printf("please input the name you want to search:");
        scanf("%s",key);
        for(i=0;i<n;i++)
        {
            if(strcmp(stu[i].studentName,key)==0)
            {
                flag="victory";
                printf("his/her ID is %ld,his/her rank is %d\n",stu[i].studentID,i+1);
                for(j=0;j<k;j++)
                {
                    printf("the score of %s is %d\n",course[j],stu[i].score[j]);
                }
            }
        }
        if(strcmp(flag,"GG")==0)
        {
            printf("error!not find!");
            fflush(stdin);
        }
    }
    //按照成绩进行对每门课程的分类
    void Setgroup(STUDENT stu[],int n,int k,char course[][12],int group[][5])
    {
        int i,j;
        for(j=0;j<k;j++)
        {
            for(i=0;i<n;i++)
            {
                if(stu[i].score[j]>=90&&stu[i].score[j]<=100)
                {
                    group[j][0]+=1;
                }
                if(stu[i].score[j]>=80&&stu[i].score[j]<90)
                {
                    group[j][1]+=1;
                }
                if(stu[i].score[j]>=70&&stu[i].score[j]<80)
                {
                    group[j][2]+=1;
                }
                if(stu[i].score[j]>=60&&stu[i].score[j]<70)
                {
                    group[j][3]+=1;
                }
                if(stu[i].score[j]<60)
                {
                    group[j][4]+=1;
                }
            }
        }
        for(i=0;i<k;i++)
        {
            printf("the number of the people that are excellent in %s is %d,its percentage is %lf%%\n",course[i],group[i][0],100*group[i][0]/(float)n);
            printf("the number of the people that are good in %s is %d,its percentage is %lf%%\n",course[i],group[i][1],100*group[i][1]/(float)n);
            printf("the number of the people that are in middle in %s is %d,its percentage is %lf%%\n",course[i],group[i][2],100*group[i][2]/(float)n);
            printf("the number of the people that are just passed in %s is %d,its percentage is %lf%%\n",course[i],group[i][3],100*group[i][3]/(float)n);
            printf("the number of the people that are not passed in %s is %d,its percentage is %lf%%\n",course[i],group[i][4],100*group[i][4]/(float)n);
        }
    }
    //打印所有数据
    void Printall(STUDENT stu[],int n,int k,char course[][12],int sums[],float avers[])
    {
            Avers(stu,sums,avers,n,k);
            int i,j;
            printf("studentID\tstudentName\t");
            for(i=0;i<k;i++)
            {
                printf("%10s\t",course[i]);
            }
            printf("total score\taverage score");
            for(i=0;i<n;i++)
            {
                printf("\n%10ld%10s",stu[i].studentID,stu[i].studentName);
                for(j=0;j<k;j++)
                {
                    printf("%18d",stu[i].score[j]);
                }
                printf("%10d\t\t%lf",sums[i],avers[i]);
            }
    }
    //将数据写入文件
    void Writetofile(STUDENT stu[],int n,int k)
    {
        int i,j;
        FILE *fp;
        if((fp=fopen("student.txt","wb"))==NULL)
        {
            printf("fail to open a file!\n");
            exit(0);
        }
        for(i=0;i<n;i++)
        {
            for(j=0;j<k;j++)
            {
                fprintf(fp,"%ld %s %d\n",stu[i].studentID,stu[i].studentName,stu[i].score[j]);
            }
        }
        fclose(fp);
    }
    //从文件中读取
    int Readfromfile(STUDENT stu[],int n,int k)
    {
        FILE *fp;
        int i,j;
        if((fp=fopen("student.txt","rb"))==NULL)
        {
            printf("fail to open a file!\n");
            exit(0);
        }
        for(i=0;i<n;i++)
        {
            for(j=0;j<k;j++)
            {
                fscanf(fp,"%ld %s %d\n",&stu[i].studentID,stu[i].studentName,&stu[i].score[k]);
            }
        }
        fclose(fp);
        printf("Total student is %d.\n",i-1);
        return i-1;
    }
