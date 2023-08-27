# Data-Structures
//linear search
#include<stdio.h>
int main()
{
	int i,num,n,j,k;
	int arr[100];
	printf("enter the size of array:");
	scanf("%d",&n);
	printf("the array is:");
	for(i=0;i<n;i++)
	{
    	scanf("%d",&arr[i]);
	}
	printf("enter the number:");
	scanf("%d",&num);
	for(j=0;j<n;j++)
	{
    	if(arr[j]==num)
	  {
		break;
	  }
	}
	if(j<n)
	{
	    printf("number found");
	}
	else
	{
	    printf("number not found");
	}
	
	
}
*****************************************************************************************************************
//linear search recurssive
#include<stdio.h>
int ls(int arr[],int num,int n,int i)
{
    if(i==n)
    {
        return -1;
    }
	if(arr[i]==num)
	{
		return i;
	}
else
{
	return ls(arr,num,n,i+1);
}
}
int main()
{
	int n,arr[100],num,i;
	printf("enter the size of array:");
	scanf("%d",&n);
	printf("enter the elements to array");
	for(i=0;i<n;i++)
	{
	  scanf("%d",&arr[i]);
    }
    printf("enter the number:");
    scanf("%d",&num);
    i=0;
    int result= ls(arr,num,n,i);
    if(result==-1)
    {
    	printf("number not found");
	}
	else
	{
		printf("number found");
	}
}
******************************************************************************************************************
//binary search
#include<stdio.h>
int main()
{
    int n,num,i,mid,start,end;
    int arr[100];
    printf("enter the size of array:");
	scanf("%d",&n);
	printf("the array is:");
	for(i=0;i<n;i++)
	{
    	scanf("%d",&arr[i]);
	}
	printf("enter the number to be searched");
	scanf("%d",&num);
	start=0;
	end=n-1;
	mid=(start+end)/2;
    while(start<=end)
	{
	    if(num==arr[mid])
	    {
	        printf("number found");
	        break;
	    }
	    else if(num<arr[mid])
	    {
	        end=mid-1;
	        mid=(start+end)/2;
	    }
	    else
	    {
	        start=mid+1;
	        mid=(start+end)/2;
	        
	    }
	}
	if(start>end)
	{
	    printf("number not found");
	}
}
************************************************************************************************************************************************
//binary search recurssive
#include<stdio.h>
int bs(int arr[100],int num,int start,int end,int n,int mid)
{
    mid=(start+end)/2;
    while(start<=end)
    {
        if(num==arr[mid])
        {
            return 1;
        }
        else if(num>arr[mid])
        {
           return bs(arr,num,mid+1,end,n,mid);
        }
        else
        {
             return bs(arr,num,start,mid-1,n,mid);
        }
    }
    if(start>end)
    {
        return 0;
    }
}
int main()
{
    int arr[100],num,mid,end,n,start,i;
    printf("enter the size of array:");
	scanf("%d",&n);
	printf("the array is:");
	for(i=0;i<n;i++)
	{
    	scanf("%d",&arr[i]);
	}
	printf("enter the number to be searched");
	scanf("%d",&num);
	start=0;
	end=n-1;
	mid=(start+end)/2;
	int result= bs(arr,num,start,end,n,mid);
	if(result==1)
	{
	    printf("element found");
	}
	else
	{
	     printf("element not found");
	}
}

************************************************************************************************************************************************
//quick sort
#include<stdio.h>
int qs(int arr[100],int first,int last)
{
 int i,pivot,temp,j;
if(first<last)
{
    
    i=first;
    j=last;
    pivot=first;
    while(i<j)
    {
        while(arr[i]<=arr[pivot] && i<last)
        i++;
        while(arr[j]>arr[pivot])
        j--;
        if(i<j)
        {
            temp=arr[i];
            arr[i]=arr[j];
            arr[j]=temp;
        }
    }
        temp=arr[pivot];
        arr[pivot]=arr[j];
        arr[j]=temp;
    qs(arr,first,j-1);
    qs(arr,j+1,last);
}
}
int main()
{
    int n,arr[100],i;
    printf("size:");
    scanf("%d",&n);
    for(i=0;i<n;i++)
    {
        scanf("%d",&arr[i]);
    }
     int first=0;
     int last=n-1;
    qs(arr,first,last);
    for(i=0;i<n;i++)
    {
        printf("%d",arr[i]);
    }
}
************************************************************************************************************************************************
//selection
#include<stdio.h>
int main()
{
    int n,arr[100],i,j,temp,min,k;
    printf("enter the size:");
    scanf("%d",&n);
    for(k=0;k<n;k++)
    {
        scanf("%d",&arr[k]);
    }
    for(i=0;i<n-1;i++)
    {
        min=i;
    for(j=i+1;j<n;j++)
     {
        if(arr[min]>arr[j])
        {
            min=j;
        }
    }
     if(min!=i)
    {
        temp=arr[i];
        arr[i]=arr[min];
        arr[min]=temp;
    }
    }
    for(k=0;k<n;k++)
    {
     printf("%d",arr[k]);
    }
}
************************************************************************************************************************************************
//insertion sort
#include<stdio.h>
int main()
{
	int i,j,temp,n, arr[100],m;
	
	printf("Enter the size of array: \n");
	scanf("%d",&n);
	
	printf("Enter the elements: \n");
	
	for(m=0; m<n; m++){
		printf("Enter the Element %d: ",m+1);
		scanf("%d",&arr[m]);
	}
		
	printf("The entered array is: ");
	for(m=0; m<n; m++){
		printf(" %d ",arr[m]);
	}
		
	for(i=1;i<n;i++)
        {
		temp =arr[i];
		j=i-1;
		while(j>=0&&temp<=arr[j])
                {
			arr[j+1]=arr[j];
			j=j-1;
		}
		arr[j+1]=temp;
	}
	printf("\n Sorted array:");
	for(m=0; m<n; m++){
		printf(" %d ",arr[m]);
		
	}
	return 0;
}
************************************************************************************************************************************************************#include <stdio.h>

// Merge two subarrays of arr[]
// First subarray is arr[l..m]
// Second subarray is arr[m+1..r]
void merge(int arr[], int l, int m, int r) {
    int i, j, k;
    int n1 = m - l + 1;
    int n2 = r - m;

    // Create temporary arrays
    int L[n1], R[n2];

    // Copy data to temporary arrays L[] and R[]
    for (i = 0; i < n1; i++)
        L[i] = arr[l + i];
    for (j = 0; j < n2; j++)
        R[j] = arr[m + 1 + j];

    // Merge the temporary arrays back into arr[l..r]
    i = 0;
    j = 0;
    k = l;
    while (i < n1 && j < n2) {
        if (L[i] <= R[j]) {
            arr[k] = L[i];
            i++;
        } else {
            arr[k] = R[j];
            j++;
        }
        k++;
    }

    // Copy the remaining elements of L[], if any
    while (i < n1) {
        arr[k] = L[i];
        i++;
        k++;
    }

    // Copy the remaining elements of R[], if any
    while (j < n2) {
        arr[k] = R[j];
        j++;
        k++;
    }
}

// Main function that sorts arr[l..r] using merge()
void mergeSort(int arr[], int l, int r) {
    if (l < r) {
        // Same as (l+r)/2, but avoids overflow for large l and r
        int m = l + (r - l) / 2;

        // Sort first and second halves
        mergeSort(arr, l, m);
        mergeSort(arr, m + 1, r);

        // Merge the sorted halves
        merge(arr, l, m, r);
    }
}

int main() {
    int arr[] = {12, 11, 13, 5, 6, 7};
    int arr_size = sizeof(arr) / sizeof(arr[0]);

    printf("Original array: ");
    for (int i = 0; i < arr_size; i++)
        printf("%d ", arr[i]);

    mergeSort(arr, 0, arr_size - 1);

    printf("\nSorted array: ");
    for (int i = 0; i < arr_size; i++)
        printf("%d ", arr[i]);

    return 0;
}
************************************************************************************************************************************************************
//bubble sort
#include<stdio.h>
int main()
{
    int arr[10]={8,5,21,80,9};
    int i,j,temp,flag;
    int n=5;
    for(i=0;i<n;i++)
    {
        int flag=0;
        for(j=0;j<n-i-1;j++)
        {
            if(arr[j]>arr[j+1])
            {
            temp=arr[j];
            arr[j]=arr[j+1];
            arr[j+1]=temp;
            flag=1;
            }
        }
        if(flag==0)
        {
            printf("the sorted list is :");
            break;
        }
    }
    for(i=0;i<n;i++)
    {
        printf(" %d ",arr[i]);
    }
}
