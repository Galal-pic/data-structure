	#include <iostream>
	#include "node.h"
	using namespace std;
	int main()
	{
		BST Test;
		Test.Insert(1);
		Test.Insert(5);
		Test.Insert(20);
		Test.Insert(4);
		Test.Insert(6);
		cout << "         Hello in my tree -_- choose : \n";
		while (true)
		{


			cout << " 1- Tree display by pre-order \n " << "2- Tree display by post-order\n" << " 3- Tree display by in - order\n" << " 4- Tree display by level-order" << endl;
			cout << " 5- search element\n" << " 6- count the nodes\n" << " 7- get minimum value in tree\n" << " 8- get the maximum value in tree\n" << " 9- delete element " << endl;
			int x;
			cout << " -> inter the number"; cin >> x;
			switch (x)
			{
			case 1:
				Test.preorder(); cout << endl;
				break;
			case 2:
				Test.postorder(); cout << endl;
				break;
				break;
			case 3:
				Test.inorder(); cout << endl;
				break;
				break;
			case 4:
				Test.levelorder(); cout << endl;
				break;
				break;
			case 5:
			{
				cout << "inter the number "; int x; cin >> x;
				if (Test.Search(x))
					cout << "found --" << endl;
				else
					cout << "not found --" << endl;
			}
			break;
			case 6:
				cout << Test.Count() << endl;
				break;
			case 7:
				cout << Test.minimum_val() << endl;
				break;
			case 8:
				cout << Test.maximum_val() << endl;;
				break;
			default:
			{
				cout << "inter the number "; int x; cin >> x;
				Test.Delete(x, Test.ROOT);

			}
			}

			cout << "Do you want to return the program ? if you want press 1 else press 0";
			int a;
			cin >> a;
			if (a == 0)
				break;
		}
	
	}

