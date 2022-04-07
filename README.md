# Gamefor2
Games such as hangman, XO
#include <iostream>
#include <cstdlib>
#include<ctime>
#include <string>
using namespace std;
const int MAX_TRIES=5;
int letterFill (char, string, string&);


int hangman ()
{
 string name;
 char letter;
 int num_of_wrong_guesses=0;
 string word;
 string words[] =
 {
 "india",
 "pakistan",
 "nepal",
 "malaysia",
 "philippines",
 "australia",
 "iran",
 "ethiopia",
 "oman",
 "indonesia"
 };

 //choose and copy a word from array of words randomly
 srand(time(NULL));
 int n=rand()% 10;
 word=words[n];

 // Initialize the secret word with the * character.
 string unknown(word.length(),'*');

 // welcome the user
 cout << "\n\nWelcome to hangman...Guess a country Name";
 cout << "\n\nEach letter is represented by a star.";

 

 cout << "\n\nYou have to type only one letter in one try";

 

 cout << "\n\nYou have " << MAX_TRIES << " tries to try and guess the word.";
 cout << "\n~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~";

 // Loop until the guesses are used up
 while (num_of_wrong_guesses < MAX_TRIES)
 {
 cout << "\n\n" << unknown;
 cout << "\n\nGuess a letter: ";
 cin >> letter;
 // Fill secret word with letter if the guess is correct,
 // otherwise increment the number of wrong guesses.
 if (letterFill(letter, word, unknown)==0)
 {
 cout << endl << "Whoops! That letter isn't in there!" << endl;
 num_of_wrong_guesses++;
 }
 else
 {
 cout << endl << "You found a letter! Isn't that exciting!" << endl;
 }
 // Tell user how many guesses has left.
 cout << "You have " << MAX_TRIES - num_of_wrong_guesses;
 cout << " guesses left." << endl;
 // Check if user guessed the word.
 if (word==unknown)
 {
 cout << word << endl;
 cout << "Yeah! You got it!";
 break;
 }
 }
 if(num_of_wrong_guesses == MAX_TRIES)
 {
 cout << "\nSorry, you lose...you've been hanged." << endl;
 cout << "The word was : " << word << endl;
 }
 cin.ignore();
 cin.get();
 return 0;
}
int letterFill (char guess, string secretword, string &guessword)
{
 int i;
 int matches=0;
 int len=secretword.length();
 for (i = 0; i< len; i++)
 {
 // Did we already match this letter in a previous guess?
 if (guess == guessword[i])
 return 0;
 // Is the guess in the secret word?
 if (guess == secretword[i])
 {
 guessword[i] = guess;
 matches++;
 }
 }
 return matches;
}


char square[9] = {'0','1','2','3','4','5','6','7','8'};
int checkwin()
{
		if (square[0] == square [1]  && square[1] == square[2] )
		{	if ( square [0] == 'X' )			
			return 1;
			else
			return 2; 
		}		
		else
		if (square[3] == square [4]  && square[4] == square[5] )
			{	if ( square [3] == 'X' )			
			return 1;
			else
			return 2; 
		}
		else
		if (square[6] == square [7]  && square[7] == square[8] )
			{	if ( square [6] == 'X' )			
			return 1;
			else
			return 2; 
		}
		else
		if (square[0] == square [3]  && square[3] == square[6] )
			{	if ( square [0] == 'X' )			
			return 1;
			else
			return 2; 
		}
		else
		if (square[1] == square [4]  && square[4] == square[7] )
			{	if ( square [1] == 'X' )			
			return 1;
			else
			return 2; 
		}
	else
		if (square[2] == square [5]  && square[5] == square[8] )
			{	if ( square [2] == 'X' )			
			return 1;
			else
			return 2; 
		}
else
		if (square[0] == square [4]  && square[4] == square[8] )
			{	if ( square [0] == 'X' )			
			return 1;
			else
			return 2; 
		}
	else
		if (square[2] == square [4]  && square[4] == square[6] )
			{	if ( square [2] == 'X' )			
			return 1;
			else
			return 2; 
		}
	else
		if (square[0] == square [3]  && square[3] == square[6] )
			{	if ( square [0] == 'X' )			
			return 1;
			else
			return 2; 
		}
	else 
		return 0;
}

void mark(int player, int box)
{
	if (player == 1 )
	{

		square[box] = 'X';
	}
	else
		square[box] = 'O';
}

void display()
{
		for(int i=0;i<9;i++)
		{
			cout<< square[i] << "\t" ;
				if (i == 2 || i== 5 || i==8)
					cout<<"\n"; 
}
}

int xo(){
    	int player1=1,player2=2;
		char p1[20],p2[20];
		int box, result = 0, flag = 0;
		cout<<"Enter 1st player name: ";
		cin>>p1;
		cout<<"Enter 2nd player name: ";
		cin>>p2;
		
		display();
		for(int i=1;i<5;i++)
	{

		cout<< "\n Player " << p1 <<"\t"<< "Enter the Box: ";
		cin>> box;

		mark( player1, box);
		display();

		result =checkwin();	
		if (result == 1 )
		{	cout<<"\n Congratualtions! player " << p1 << " has Won ";
			flag = 1;			
			break;
		}
		else
		if (result == 2 )
		{	cout<<"\n Congratualtions! player " << p2 << " has Won ";
			flag = 1;			
			break;
		}
		cout<< "\n Player " << p2<<"\t" << "Enter the Box: ";
		cin>> box;
		if (box == 'Q'){
		    cout<<"Thank you for playing!! ";
		    break;
		    
		}
		mark ( player2, box);
		display();
		
		result =checkwin();	
		if (result == 1 )
		{	cout<<"\n Congratualtions! player " << p1 << " has Won ";
			flag = 1;
			break;
		}
		else
		if (result == 2 )
		{	cout<<"\n Congratualtions! player " << p2 << " has Won ";
			flag = 1;
			break;
		}
}
		if (flag == 0 )
		cout<<" \n Sorry, The game is a draw ";
	
	return 0;
}

int main()
{
	int answer;
	cout<<"****Welcome to the gameboy!!**** \n";
	cout<<"Here is the list of games \n";
	cout<<"1. Hangman"<<endl;
	cout<<"2. X and O"<<endl;
	cout<<"Which game do you want to play?"<<endl<<" Type the number:";
	cin>>answer;
	switch(answer){
	    case 1: hangman();
	            break;
	    case 2: xo();
	            break;
	    default: cout<<"Please choose a valid option";
	    
	}


}
