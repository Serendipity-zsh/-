**题目：**

给定一个字符串，找到它的第一个不重复的字符，并返回它的索引。如果不存在，则返回 -1。

**示例：**

> s = "leetcode", 
>
> 返回 0.
>
> s = "loveleetcode",
>
> 返回 2.

**思路和方法：**

首先解释一下题目中的索引是string类中的说法，其实他的意思就是我们数组中的下标值。

其实这道题思路很简单无非就是把字符串中的字符挨个的比一遍，不过我们就是要保证返回值的唯一性，也就是问题中所说字符串中的第一个没有重复的字符。那么我们就用两个循环从第一个字符开始与其他字符比较，取一个控制变量count=0，有重复就加1，内部循环结束后判断count的值是否改变，没有改变那就是我们想要的答案，返回下标值即可，为了保证唯一性，这时候我i们需要结束整个循环，所以用exit(0)，终止程序；如果整个循环结束没找到我们想要的，那么就返回-1。

**代码如下：**

有几种不同的表示方法，但思路都是一样的。

```cpp
//这两个是基于C++的形式

//用字符串表达
class Soulution{
	public:
		int result(string s)
		{
			int n=s.length();           //length()是string类的成员函数，功能是返回字符串的长度(字符个数) 
			int count=0;
			for(int i=0;i<n-1;i++)
			{
				for(int j=i+1;j<n;j++)
				{
					if(s[i]=s[j])
					{
						count++;
					}
				}
				if(count==0)
				{
					return i;
					exit(0);         //exit(0)函数正常表示终止程序 
				} 
			}
			return -1;
		}
};

//用vector字符数组表达
class Solution{
       public:
              int result(vector<char> &s) 
              {
	          int n=s.size();                  //调用size()函数返回数组s的大小
	          int count=0;
	          for(int i=0;i<n-1;i++)
	          {
		        for(int j=i+1;j<n;j++)
		        {
			    if(s[i]=s[j])
			    {
				count++;
			    }
	                }
			if(count==0)
			{
				return i;
				exit(0);         //exit(0)函数正常表示终止程序 
			} 
	          }
	          return -1;
              }
};
```

![点击并拖拽以移动](data:image/gif;base64,R0lGODlhAQABAPABAP///wAAACH5BAEKAAAALAAAAAABAAEAAAICRAEAOw==)

```cs
//这两个是基于C的

int result(char *s)
{
	int i,j,n;
	int count=0;
	n=strlen(s);          //strlen()函数返回字符串s的长度 
	for(i=0;i<n-1;i++)
	{
		for(j=i+1;j<n;j++)
		{
			if(s[i]=s[j])
			{
				count++;
			}
		}
		if(count==0)
		{
			return i;
			exit(0);      //exit(0)函数正常表示终止程序
		}
	}
	return -1;
}


int result(char *s)
{
	int i,j,n;
	int count=0;
	n=strlen(s);          //strlen()函数返回字符串s的长度 
	for(i=0;i<n-1;i++)
	{
		for(j=i+1;j<n;j++)
		{
			if(*(s+i)=*(s+j))
			{
				count++;
			}
		}
		if(count==0)
		{
			return i;
			exit(0);      //exit(0)函数正常表示终止程序
		}
	}
	return -1;
}
```

