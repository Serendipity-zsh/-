**题目：**

给定一个 *m* x *n* 的矩阵，如果一个元素为 0，则将其所在行和列的所有元素都设为 0。请使用**原地**算法**。**

**示例1：**

> **输入:** [   [1,1,1],   [1,0,1],   [1,1,1] ]
>
> **输出:** [   [1,0,1],   [0,0,0],   [1,0,1] ]

**示例2：**

> **输入:** [   [0,1,2,0],   [3,4,5,2],   [1,3,1,5] ]
>
> **输出:** [   [0,0,0,0],   [0,4,5,0],   [0,3,1,0] ]

**进阶:**

- 一个直接的解决方案是使用  O(*m**n*) 的额外空间，但这并不是一个好的解决方案。
- 一个简单的改进方案是使用 O(*m* + *n*) 的额外空间，但这仍然不是最好的解决方案。
- 你能想出一个常数空间的解决方案吗？

**思路：**

这道题我刚开始的时候是想错了的，我先说一下我的错误的方法，可能会有人跟我的错误一样**。**

思路就是两个循环把二维矩阵的元素访问一遍，找出其中数值为0的位置，然后记录行列位置，再用两个循环把之前记录的行列的所有元素都置零。

**错误代码如下：**

```cpp
class Solution{
	public:
		void result(vector<vector<int>>& matrix)
		{
			int m=matrix.size();       //m表示矩阵matrix的行数
			int n=matrix[0].size();    //n表示矩阵matrix的列数
			int p,q;
			for(int i=0;i<m;i++)
			{
				for(int j=0;j<n;j++)
				{
					if(matrix[i][j]==0)
					{
						p=i;
						q=j;
					}
				}
			}
			for(int i=0;i<n;i++)
			{
				for(int j=0;j<m;j++)
				{
					if(i==p||j==q)
					{
						martix[i][j]=0;
					}
				}
			}
		}
}; 
```

![点击并拖拽以移动](data:image/gif;base64,R0lGODlhAQABAPABAP///wAAACH5BAEKAAAALAAAAAABAAEAAAICRAEAOw==)

然后我就在leetcode上测试了一下，结果是对的，但是我提交了一下发现错了，

这是为什么呢？

原因很简单，大家看一下示例2，矩阵中有两个0，这时候上述代码中的p和q最终记录的最后的那个，p和q只能记录一个值，所以很显然上面那个代码是不对的。现在我们要解决的问题是如何记录多个数值为0的位置，首先我考虑的是用两个整型，然后发现还是不行，数组的长度和初始化问题无法解决，最后搜了一下，然后有看了看书，决定用bool型数组，长度分别是原矩阵的行列数，当矩阵中某个位置为0时，就把两个bool型数组在该位置的元素置为真，下面的·就跟之前的没什么区别了。

**代码如下：**

```cpp
class Solution {
public:
    void result<vector<int>>& matrix) 
    {
        int m=matrix.size();          //m表示矩阵matrix的行数
	int n=matrix[0].size();       //n表示矩阵matrix的列数
	vector<bool> p(m);            //创建bool型的数组，长度分别是矩阵matrix的行列数
        vector<bool> q(n);
	for(int i=0;i<m;i++)
	{
	    for(int j=0;j<n;j++)
	    {
		if(matrix[i][j]==0)
		{
			p[i]=true;
                        q[j]=true;
		}
	    }
	}
        for(int i=0;i<m;i++)
        {
            for(int j=0;j<n;j++)
            {
                if(p[i]==true||q[j]==true)
                {
                    matrix[i][j]=0;
                }
            }
        }
    }
};
```

