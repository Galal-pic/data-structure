#include "node.h"
#include <iostream>
#include<queue>
using namespace std;
void BST::Insert(node *&cur, int v)
{
	if (cur == NULL) // base case (in this line creat the node in same time linked)
		cur = new node(v);
	else
	{
		if (v <= cur->value)
		{
			Insert(cur->left, v);
			cur->left->parent = cur;
		}
		else
		{
			Insert(cur->right, v);
			cur->right->parent = cur;
		}
	}
}
void BST::Insert(int x)
{
	Insert(ROOT, x);
}
void BST::preorder(node *cur)
{
	if (cur == NULL)
		return;
	cout << cur->value << " ";
	preorder(cur->left);
	preorder(cur->right);
}
void BST::preorder()
{
	preorder(ROOT);
}
void BST::inorder(node *cur)
{
	if (cur == NULL)
		return;
	inorder(cur->left);
	cout << cur->value << " ";
	inorder(cur->right);
}
void BST::inorder()
{
	inorder(ROOT);
}

void BST:: postorder(node *cur)
{
	if (cur == NULL)
		return;
	postorder(cur->left);
	postorder(cur->right);
	cout << cur->value << " ";
}
void BST::postorder()
{
	postorder(ROOT);
}
void BST::levelorder(node *cur)
{
	if (cur == NULL)
		return;
	queue<node*>q;
	q.push(cur);
	while (!q.empty())
	{
		node*r = q.front();
		cout << r->value << " ";
		if (r->left != NULL)
			q.push(r->left);
		if (r->right != NULL)
			q.push(r->right);
		q.pop();
	}
}
void BST::levelorder()
{
	levelorder(ROOT);
}
bool BST::Search(int x, node *cur)
{
	node *ptr = cur;
	while (ptr)
	{
		if (ptr->value == x)
			return true;
		else if (x > ptr->value)
			ptr = ptr->right;
		else
			ptr = ptr->left;
	}
	cout << "No found ....." << endl;
	return false;
}
bool BST::Search(int a)
{
	return Search(a, ROOT);
}
int BST:: Count(node *cur)
{
	static int num = 0;
	if (cur)
	{
		Count(cur->left);
		Count(cur->right);
		num++;
	}
	return num;
}
int BST::Count()
{
	return Count(ROOT);
}
int BST::minimum_val(node *cur)
{
	if (cur->left == NULL)
		return cur->value;
	return minimum_val(cur->left);
}
int BST::minimum_val()
{
	return minimum_val(ROOT);
}
int BST::maximum_val(node *cur)
{
	if (cur->right == NULL)
		return cur->value;
	return maximum_val(cur->right);
}
int BST::maximum_val()
{
	return maximum_val(ROOT);
}
int BST::get_successor(node*cur, node*place)
{
	if (place->right != NULL)
		return minimum_val(place->right);
	node*p = place->parent;
	while (p != NULL && place == p->right)
	{
		place = p;
		p = p->parent;
	}
	return p->value;
}
int BST::Height(node *ptr)
{
	int x, y;
	if (ptr == NULL)
		return 0;
	x = Height(ptr->left);
	y = Height(ptr->right);
	return x > y ? x + 1 : y + 1;
}
node *BST::InPre(node *ptr)
{
	if (ptr->right != NULL)
		return InPre(ptr->right);
	return ptr;
}
node *BST::InSucc(node *ptr)
{
	if (ptr->left != NULL)
		return InSucc(ptr->left);

	return ptr;
}
node *BST::Delete(int v, node *&ptr)
{
	node *ptr2;

	if (ptr == NULL) //for empty BST.
		return NULL;

	if (v < ptr->value)
		ptr->left = Delete(v, ptr->left); //go left.
	else if (v > ptr->value)
		ptr->right = Delete(v, ptr->right); //go right.
	else
	{
		if (ptr->left == NULL && ptr->right == NULL) //for a leaf node.
		{
			delete ptr;
			return NULL;
		}
		if (Height(ptr->left) > Height(ptr->right)) //for non leaf node .
		{
			ptr2 = InPre(ptr->left);
			ptr->value = ptr2->value;
			ptr->left = Delete(ptr2->value, ptr->left);
		}
		else     //for non leaf node.
		{
			ptr2 = InSucc(ptr->right);
			ptr->value = ptr2->value;
			ptr->right = Delete(ptr2->value, ptr->right);
		}
	}
	return ptr;
}