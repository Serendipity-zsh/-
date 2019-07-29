**题目：**

给定两个有序整数数组 *nums1* 和 nums2，将 *nums2* 合并到 *nums1* 中*，*使得 *num1* 成为一个有序数组。

**说明:**

初始化 *nums1* 和 *nums2* 的元素数量分别为 *m* 和 *n*。

你可以假设 *nums1* 有足够的空间（空间大小大于或等于 *m + n*）来保存 *nums2* 中的元素。

**示例：**

> **输入:** nums1 = [1,2,3,0,0,0], m = 3
>
> nums2 = [2,5,6], n = 3
>
> **输出:** [1,2,2,3,5,6]

**思路：**

对于这道题我自己的思路很简单，而且自我感觉很容易实现。大致如下：

定义一个新的动态整型数组，然后把题目中初始化的两个数组依次的初始化给这个新的数组，然后在把这个新的数组按照题目规定重新排序，最后返回这个数组，即可得到题目想要的答案。但是我这个方法是比较笨的方法，因为在前面的说明中我们可以看出这个题的意思其实是想让我们把数组nums2并入nums1中，而且这两个数组已经是有序数组了。所以针对这题还有一种比较简单的方法，下面我会依次给出两种方法的代码。

**代码如下：**

```cpp
//用C++中的vector创建动态数组 
class Solution{
	public:
		vector<int> result(vector<int>& nums1,int m,vector<int>& nums2,int n)
		{
			vector<int> nums;
			int sum=m+n-1;
			for(int i=0;i<=sum;i++)
			{
				if(i<=m-1)
				{
					nums[i]=nums1[i];
				}
				else
				{
					nums[i]=nums2[i-m]
				}
			}
			bubbleSort(nums,n+m);         //冒泡排序 
			return nums;
		}
}; 

//用C中整型指针
int* result(int *nums1,int m,int *nums2,int n)
{
	int *nums;
	int sum=m+n-1;
	for(int i=0;i<=sum;i++)
	{
		if(i<=m-1)
		{
			nums[i]=nums1[i];
		}
		else
		{
			nums[i]=nums2[i-m]
		}
	}
	bubbleSort(nums,n+m);               //冒泡排序 
	return nums;
}

//冒泡排序函数
void bubbleSort(int a[],int n)
{
    int i=n-1;
	while(i>0)
	{
	    int exchange=0;
	    for(int j=0;j<i;j++)
	    {
	    	if(a[j+1]<a[j])
	    	{
	    		mySwap(a[j],a[j+1]);
	    		exchange=j;
			}
			i=exchange;
		}
	} 	
}
void Swap(int &x,int &y)
{
	int temp=x;
	x=y;
	y=temp;
}
```

![点击并拖拽以移动](data:image/gif;base64,R0lGODlhAQABAPABAP///wAAACH5BAEKAAAALAAAAAABAAEAAAICRAEAOw==)

```cpp
//从后往前进行排序   

void result(vector<int>& nums1, int m, vector<int>& nums2, int n)
{
        int sum=m+n-1;
        m-=1;
        n-=1;
        while(m>=0&&n>=0)
        {
            if(nums2[n]>nums1[m])
            {
                nums1[sum]=nums2[n];
                sum--;
                n--;
            }
            else
            {
                nums1[sum]=nums1[m];
                sum--;
                m--;
            }
        }
        while(n>=0)
        {
            nums1[sum]=nums2[n];
            sum--;
            n--;
        }
}
```

