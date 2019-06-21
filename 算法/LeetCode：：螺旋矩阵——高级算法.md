**题目：**

给定一个包含 *m* x *n* 个元素的矩阵（*m* 行, *n* 列），请按照顺时针螺旋顺序，返回矩阵中的所有元素。

**示例1：**

> **输入:**[  [1, 2, 3],  
>
> ​           [ 4, 5, 6 ],
>
> ​           [ 7, 8, 9 ] ]
>
> **输出:** [1,2,3,6,9,8,7,4,5]

**示例2：**

> **输入:** [  [1, 2, 3, 4],
>
> ​             [5, 6, 7, 8],
>
> ​             [9,10,11,12] ]
>
> **输出:** [1,2,3,4,8,12,11,10,9,5,6,7]

**思路方法：**

这道题在我只看题目和示例之后，感觉还挺简单的，不就是把矩阵按照顺时针的顺序依次赋值给一个整形数组，然后最后返回这个数组。但是当我用代码去实现的时候，发现并没有我想的那么简单，首先因为不知道矩阵的行和列，不可能一个一个的传值给整型数组，所以我想了想，决定写一下按照顺时针传值的步骤，找一下其中的规律，大致分为四步，分别是：从第一行第一个到第一行最后一个；从第二行最后一个到最后一行最后一个；从最后一行倒数第二个到最后一行第一个；从倒数第二行第一个到第二行第一个；这就算是顺时针最外围的一个循环，然后后面的跟前面的是类似的不过循环的行和列都少1，大致的规律就是这样，还需要设置一个全局变量，用来做返回数组的下标值。在每一小步的循环里加一个bool型标量，用来判断四个步骤是否被执行，如果没有被执行就说明矩阵的值已经传输完毕，就可以结束整个循环了。

**代码如下：**

```cpp
class Solution{
	public:
		vector<int> result(vector<vector<int> >& matrix)
		{
			vector<int> nums;
			int m=matrix.size();       //m表示的是矩阵matrix的行数
			int n=matrix[0].size();    //n表示的是矩阵matrix的列数
			int count=0;               //全局变量count用来表示数组nums的下标值
			do 
		    {
			    int j=0;
		            bool judge=false;       //用来判断是否结束整个循环
			    bool a=false;           //a，b，c，d分别判断四个步骤是否被执行
			    bool b=false;
			    bool c=false;
			    bool d=false;
			    for(int i=j;i<n-j;i++)
			    {
				    nums[count]=matrix[j][i];
				    count++;
				    a=true;
	                   }
			   for(int i=j+1;i<m-j;i++)
			   {
				  nums[count]=matrix[i][n-j-1];
				  count++;
				  b=true;
			   }
			   for(int i=n-j-2;i>=j;i--)
			   {
				  nums[count]=matrix[m-j-1][i];
			  	  count++;
			  	  c=true;
			   }
			   	for(int i=m-j-2;i>=j+1;i--)
			    {
				    nums[count]=matrix[i][j];
				    count++;
				    d=true;
			    }
			    j++;
			    if(a&&b&&c&&d)
			    {
			    	judge=true;
				}
		    }while(judge);
		    return nums;
		}
};
```
