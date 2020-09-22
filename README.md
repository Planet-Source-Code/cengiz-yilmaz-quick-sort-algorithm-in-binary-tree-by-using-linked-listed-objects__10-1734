<div align="center">

## Quick sort algorithm in binary tree \(by using linked listed objects\)


</div>

### Description

The main purpose of this code is to sort elements without given any predefined value. Therefore result is like a binary tree.
 
### More Info
 
number of elements you want to sort and elements

Sorted elements

no side effects


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[Cengiz YILMAZ](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/cengiz-yilmaz.md)
**Level**          |Beginner
**User Rating**    |5.0 (15 globes from 3 users)
**Compatibility**  |C\#
**Category**       |[Algorithims](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/algorithims__10-29.md)
**World**          |[\.Net \(C\#, VB\.net\)](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/net-c-vb-net.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/cengiz-yilmaz-quick-sort-algorithm-in-binary-tree-by-using-linked-listed-objects__10-1734/archive/master.zip)





### Source Code

```
/*
 * This program sorts the given number of elements
 * by using quick sort algorthim. But this algorithm
 * applies to like a linked listed objects instead of
 * contigous array. Therefore results of this algorithm
 * gives you a binary tree and you can sort any number of
 * elements.
 */
using System;
namespace quicksort
{
	/// <summary>
	/// Summary description for Class1.
	/// </summary>
	class Class1
	{
		/// <summary>
		/// The main entry point for the application.
		/// </summary>
		[STAThread]
		static void Main(string[] args)
		{
			int j,k;
			Node nd=new Node();
			//Number of sorting element is entered here
			Console.WriteLine("Please Enter number of sorting element");
			j=Int32.Parse(Console.ReadLine());
			//all elements is writen in a node object. Node object have next and previous attributes also in node object.
			nd=valueread(nd,j);
			k=nd.getnextnode().getvalue();
			//sorting algorithm is called here
			nd=qsort(nd);
			Console.WriteLine("Results are below"+nd.getvalue());
			showresult(nd);
			Console.ReadLine();
		}
		//This function reads the datas and writes them to a linked list node object
		public static Node valueread(Node nd,int i)
		{
			Node parnt=new Node();
			parnt=nd;
			for(int k=0;k<i;++k)
			{
				Console.WriteLine("Please Enter value of the "+ k+ " th element");
				nd.addnumber(Int32.Parse(Console.ReadLine()));
				if(k!=i-1)
				{
					Node temp=new Node();
					nd.setnext(temp);
					temp.setprevious(nd);
					nd=temp;
				}
			}
			nd=parnt;
			return nd;
		}
		public static void showresult(Node nd)
		{
			if(nd.getleftnode()!=null)
				showresult(nd.getleftnode());
			Console.WriteLine(nd.getvalue());
			if(nd.getrightnode()!=null)
				showresult(nd.getrightnode());
		}
		//This function sorts the elements by using quick sort and
		// output is binary tree.
		public static Node qsort(Node nd)
		{
			int i=0;
			Node parent=new Node();
			Node nleft=new Node();
			Node nright=new Node();
			parent=nd;
			Node temp=new Node();
			temp=nd.getnextnode();
			nd.setnext(null);
			if(temp!=null)
			{
				do
				{
					if(temp.getvalue()<=parent.getvalue())
					{
						if(parent.getleftnode()==null)
						{
							parent.setleftnode(temp);
							temp.setparentnode(parent);
							nleft=temp;
						}
						else
						{
							nleft.setnext(temp);
							nleft=temp;
						}
					}
					else
					{
						if(parent.getrightnode()==null)
						{
							parent.setrightnode(temp);
							temp.setparentnode(parent);
							nright=temp;
						}
						else
						{
							nright.setnext(temp);
							nright=temp;
						}
					}
					temp.setprevious(null);
					if(temp.getnextnode()!=null)
					{
						temp=temp.getnextnode();
					}
					else
						i=1;
				}while(i!=1);
				nleft.setnext(null);
				nright.setnext(null);
			}
			if(parent.getleftnode()!=null)
				qsort(parent.getleftnode());
			if(parent.getrightnode()!=null)
				qsort(parent.getrightnode());
			nd=parent;
			return nd;
		}
	}
/* Node objects are created in here.
 * A node have next,previous attributes
 * which are also node class for gathering the elements
 * Also this node class have parent,left,right node which are also node
 * class for using quick sort algorithms.
 */
	public class Node
	{
		private Node left;
		private Node right;
		private Node parent;
		private Node next;
		private Node previous;
		private int number;
		public Node()
		{
			number=0;
		}
		public void addnumber(int i)
		{
			number=i;
		}
		public int getvalue()
		{
			return number;
		}
		public Node getnextnode()
		{
			return next;
		}
		public Node getleftnode()
		{
			return left;
		}
		public Node getrightnode()
		{
			return right;
		}
		public Node getparentnode()
		{
      return parent;
		}
		public void setleftnode(Node tnode)
		{
			if(tnode!=null)
				left=tnode;
			else
				left=null;
		}
		public void setrightnode(Node tnode)
		{
			if(tnode!=null)
				right=tnode;
			else
				right=null;
		}
		public void setparentnode(Node tnode)
		{
			parent=tnode;
		}
		public void setnext(Node tnode)
		{
			if(tnode!=null)
				next=tnode;
			else
				next=null;
		}
		public void setprevious(Node tnode)
		{
			if(tnode!=null)
				previous=tnode;
			else
				previous=null;
		}
	}
}
```

