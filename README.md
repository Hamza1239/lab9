# lab9
#include<iostream>
#include<stack>
#include<string>
using namespace std;
// Function to check whether two characters are opening 
// and closing of same type. 
bool ArePair(char opening,char closing)
{
	if(opening == '(' && closing == ')') return true;
	else if(opening == '{' && closing == '}') return true;
	else if(opening == '[' && closing == ']') return true;
	return false;
}
bool AreParanthesesBalanced(string exp)   // Validataion of Parenthesis 
{
	stack<char>  S;
	for(signed int i =0;i<exp.length();i++)
	{
		if(exp[i] == '(' || exp[i] == '{' || exp[i] == '[')    // if start with ( must end with )
			S.push(exp[i]);
		else if(exp[i] == ')' || exp[i] == '}' || exp[i] == ']')
		{
			if(S.empty() || !ArePair(S.top(),exp[i]))
				return false;
			else
				S.pop();
		}
	}
	return S.empty() ? true:false;
}

int main()
{
	/*Code to test the function AreParanthesesBalanced*/
	string expression;
	char extra1[10];
	char extra2[10];
	signed int x=1, y = 1,counter = 0,arrc2 = 0;
	int j=0,k=0;
	char arr[10];
	char arr2[10];
	cout<<"Enter an expression:  "; // input expression from STDIN/Console
	cin>>expression;
	if(AreParanthesesBalanced(expression))
	{
	    cout<<"Balanced\n";
	    int count;
	    for(int i =0; i<expression.length();i++)   // loop for spliting before and after =
	    {
	        if(expression[i] == '=')
	        count = i;
	       
	    }
	    
	    
	    for(int i =0; i < count; i++)           // loop for filling the data in array before = sign
	    { 
	       
	         arr[i] = expression[i];
	   
	         counter++;
	         
	    }
	   
	   
	    for(int i = 0; i <expression.length(); i++)       // loop for filling the data in array after = sign
	    { 
	       
	         if(expression[i] == '=')
	        {
	           y = 0;
	        }
	        
	        if(y == 0) 
	        { 
	            
	            arr2[j] = expression[i+1];
	      
	         arrc2++;
	         j++;
	        }
	    }
	   
	    
	    for(int i =0; i < counter; i++)        // loop for finding the data in array separeted by + or -
	    {
	        int p = arr[i];
	        if(p == '+' || p == '-')
	        {
	           x = 0;
	        }
	        
	        
	        if (x == 1)
	        {
	         extra1[i] = arr[i];
	        }
	        else if ( x == 0)
	        {
	            
	            extra2[k] = arr[i];
	            k++;
	        }
	        
	    }
	    
	    
	    if(extra2[0] == '+')        // condition for appending opposite sign in case of shuffling toward =
	    {
	        extra2[0]='-';
	    }else if (extra2[0] == '-')
	    {
	        extra2[0]='+';
	    }
	
        int t = atoi(arr2);
      
	    int l = atoi(extra2);
	  
	  cout << extra1[0];       // Printing of Results
	  cout << extra1[1];       // Printing of Results
	  cout << "=";       // Printing of Results
	  cout << t;       // Printing of Results
	  cout << l <<endl;       // Printing of Results
	  
        int o;       // Printing of Results
        o = t+l;       // Printing of Results
        
         cout << extra1[0];       // Printing of Results
	     cout << extra1[1];       // Printing of Results
	     cout << "=";       // Printing of Results
	     cout << o <<endl;       // Printing of Results
	     
	    
	     float r = 0;
	     char q = extra1[0];
	     char array[10];
	     array[0] = q;
	     float v = atoi(array);
	     r = o/v;
	     
	     cout << arr[1] << "=" << r <<endl;              // Printing of Final Results
	}
	else
		cout<<"Not Balanced\n";
}
