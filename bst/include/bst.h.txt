#pragma once
#include<iostream>
using namespace std;
class node
{
public:
	int value;
	node*left = 0;
	node*right = 0;
	node*parent = 0;
	node(int x)
	{
		value = x;
	}
	node(){} //empty constructor 
};
class BST
{
public :
	node *ROOT;
	BST(node *root = NULL)
	{
		this->ROOT = root;
	}
	void Insert(node *&, int );  // insert element in tree
	void Insert(int);
	void preorder(node *); //print (root - left- right)
	void preorder();
	void postorder(node *);     //print (left - right - root)
	void postorder();    
	void inorder(node *);      //print (left - root - right)
	void inorder();
	void levelorder(node *);  // print level by level
	void levelorder();  // print level by level
	bool Search(int , node *);// search the X int the tree and return true || false 
	bool Search(int a);
	int Count(node *);        // count numbers of nodes in tree
	int Count();
	int minimum_val(node *);  // return the min number
	int minimum_val();  // return the min number
	int maximum_val(node *); // return the min number
	int maximum_val(); // return the min number
	int get_successor(node*, node*);
	int Height(node *);
	node *InPre(node *);
	node *InSucc(node *);
	node *Delete(int , node *&);

};
