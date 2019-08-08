**题目：**
在未排序的数组中找到第 **k** 个最大的元素。请注意，你需要找的是数组排序后的第 k 个最大的元素，而不是第 k 个不同的元素。

**示例1：**

> **输入:** `[3,2,1,5,6,4] 和` k = 2
>
> **输出:** 5

**示例2：**

> **输入:** `[3,2,3,1,2,4,5,5,6] 和` k = 4
>
> **输出:** 4

**说明:** 

你可以假设 k 总是有效的，且 1 ≤ k ≤ 数组的长度。

**思路方法：**

这道题思路就挺简单的，考查的就是对排序算法的了解。按照leetcode上代码行的提示，需要用C++的语法，如果用其他的貌似不能通过。所以我就用C++语法来写。用vector创建一个一维动态数组，初始化数组后，就用排序算法把数组元素按照降序排列，最后返回排序好的数组中下标为k-1的元素即是答案。

那我就分别写三种排序的算法吧。

**代码如下：**

```
//插入排序
class Solution{
	public:
		int result(vector<int>& nums,int k)
		{
			int n=nums.size();          //调用size()函数返回数组元素个数  
			int temp;
			for(int i=1;i<n;i++)
			{
				int j=i;
				temp=nums[i];
				while(j>0;&&temp>nums[j-1])
				{
					nums[j]=nums[j-1];
					j--;
				}
				nums[j]=temp;
			}
			return nums[k-1];
		}
};

//选择排序
class Soultion{
	public:
		int result(vector<int>& nums,int k)
		{
			int n=nums.size();          //调用size()函数返回数组元素个数
			int temp;
			for(int i=0;i<n-1;i++)
			{
				int least=i;
				for(int j=i+1;j<n;j++)
				{
					if(nums[j]>nums[least])
					{
						least=j;
					}
			    }
				temp=nums[j];
				nums[j]=nums[least];
				nums[least]=temp;
			}
			return nums[k-1]; 
		}
}; 

//冒泡（起泡、交换）排序
class Solution {
public:
    int result(vector<int>& nums, int k) 
	{
                int n=nums.size();        //调用size()函数返回数组元素个数
		int i=n-1;
		int temp;
		while(i>0)
		{
			int exchange=0;
			for(int j=0;j<i;j++)
			{
				if(nums[j+1]>nums[j])
				{
					temp=nums[j+1];
					nums[j+1]=nums[j];
					nums[j]=temp;
					exchange=j+1;
				}	
			}
            i=exchange;
		}
		return nums[k-1];
    }
};
```

![点击并拖拽以移动](data:image/gif;base64,R0lGODlhAQABAPABAP///wAAACH5BAEKAAAALAAAAAABAAEAAAICRAEAOw==)

