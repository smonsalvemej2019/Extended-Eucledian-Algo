# Extended-Eucledian-Algo
code for the EEA algorithm

#include <iostream>
using namespace std;

//This programs asks for two numbers as an input and will return the GCD of the
// two numbers as well as t and s from the formula GCD(a,b) = s*a+t*b


//function prototype of the Extended Euclidean Algo
void eealgo(int a, int b, int& t, int& s);


int main() {

	//while loop is used to prevent the program from instantly closing after its done
	int select = 1;
	while (select != 0)
	{
		//variable declaration
		int t;
		int s;
		int a;
		int b;

		//Initialization of a and b
		cout << "This Program will find the GCD of two numbers" << endl;
		cout << "Input the first integer: ";
		cin >> a;
		cout << "\nInput the second integer: ";
		cin >> b;

		//if statment switches the values of a and b if b is bigger than a
		if (b > a)
		{
			int temp = a;
			a = b;
			b = temp;
		}

		//function call of the Extended Euclidean Algo
		eealgo(a, b, t, s);

		//Output of t and s
		cout << "\n(t , s) = " << t << " , " << s <<endl;

		//condition to end while loop
		cout << "\ninput 0 to end the program" <<endl;
		cin >> select;
	}
}

//Function definition of the Extended Euclidean Algo
void eealgo(int a, int b, int& t, int& s) {

	//declaration of in function variables
	int q;
	int old_s;
	int old_t;
	int r;
	int old_r;
	int tmp;

	//initialization of in function variables as well as t and s
	s = 0;
	old_s = 1;
	t = 1;
	old_t = 0;
	r = a;
	old_r = b;

	//while loop will stop when a mod b reaches 0
	while (r != 0) {

		q = old_r / r;

		tmp = r;
		r = old_r - (q * r);
		old_r = tmp;


		tmp = s;
		s = old_s - (q * s);
		old_s = tmp;


		tmp = t;
		t = old_t - (q * t);
		old_t = tmp;
	}

	//outputs the GCD
	cout << "\nCGD: " << old_r;

	//returns t as old_t and s as old_s; Both t and s are passed by refrence
	t = old_t;
	s = old_s;
}
