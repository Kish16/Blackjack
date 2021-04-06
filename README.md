# Blackjack
#include <iostream>
#include <iomanip>
#include <ctime>    // For time()
#include <cstdlib>  // For srand() and rand()

using namespace std; 
int main()

{
	int card1, card2, card3, card4, card5, card6, dealertotal, yourtotal, bet, cash;
	char decision = 'y';
	srand (time(0));
	
	cout << "----------------------";
	cout <<"\nWelcome to Blackjack!\n";
	cout << "----------------------\n\n";
	cout << "How much money are you willing to spend on Blackjack? $";
	cin >> cash;
	while (cash <= 0)
		{
			cout << "Error. You have to spend more than that!\n";
			cout << "How much money are you willing to spend on Blackjack? ";
			cin >> cash;
		}
	
	while(decision == 'y' && cash > 0)
	{
		card1 = (rand() % 10)+ 1;
		card2 = (rand() % 10) + 1;
		card3 = (rand() % 10) + 1;
		card4 = (rand() % 10) + 1;
	
		cout << "\nDealer's cards are ";
		cout << "X and "<<card2;
		cout << "\nYour cards are " << card3 << " and " << card4 << "\n";
		
		
		cout << "How much would you like to bet this round? $";
		cin >> bet;

		while (bet <= 0 || bet > cash)
		{
			cout << "Error. Invalid amount!\n";
			cout << "How much would you like to bet this round? $";
			cin >> bet;
		}
		dealertotal = card1 + card2;
		yourtotal = card3 + card4;
	
		cout << "\nWould you like another card (y/n)?";
		cin >> decision;
	
		while (decision == 'y' && yourtotal <= 21)
		{
			card5 = (rand() % 10) + 1;
			cout << "Your card is " << card5;
			yourtotal += card5;
			cout << "\nYour total is " << yourtotal;
			if(yourtotal <= 21)
			{
				cout << "\nWould you like another card (y/n)?";
				cin >> decision;
			}
		}
		
		if (yourtotal > 21)
		{
			cout << "\nYou busted. You lose\nYou lost $" << bet;
			cash = cash - bet;
		}
		
		else
		{
			cout << "\nThe dealer's cards are " << card1 << " and " << card2;
			cout << "\nThe dealer's total is " << dealertotal << "\n";
	
			while (dealertotal < 17)
			{
				card6 = (rand() % 10) + 1;
				cout << "Dealer takes a " << card6 << "\n";
				dealertotal = dealertotal + card6;
			}
			
			cout << "\nThe dealer's total is " << dealertotal << "\n";
			
			if(dealertotal > 21)
			{
				cout << "\nDealer busted. You win.\nYou gained $"<< bet;
				cash = cash + bet;
			}
			else if(yourtotal < dealertotal)
			{ 
				cout << "\nThe dealer wins! You lose!\nYou lost $" << bet;
				cash = cash - bet;
			}
		
			else if (yourtotal > dealertotal)
			{
				cout << "\nYou win.\nYou gained $" << bet;
				cash = cash + bet;
			}
			else
				cout  << "You tied with the dealer.";
		}
		
		cout << "\nYou have $" << cash << " left!\n";
		
		if (cash > 0)
		{
			cout << "Would you like to play again?(y/n) ";
			cin >> decision;
		}
				
		system("CLS");
		
		if(cash <= 0)
		{
			system ("PAUSE");
			cout << "Thanks for spending all your money! :)\n";
		}
	}
	
	system ("PAUSE"); 
	return 0;
} 

