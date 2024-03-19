# Game-Section
## XOXO Round
import java.util.*;

public class xoxo {
	static String[] board;
	static String turn;
	
	//pattern for winner check.
	static String alotWinner()//checkwinner
	{
		for(int a=0;a<8;a++)
		{
			String line =null;
			switch(a) {
			case 0: line=board[0]+board[1]+board[2];
			break;
			case 1: line=board[3]+board[4]+board[5];
			break;
			case 2: line=board[6]+board[7]+board[8];
			break;
			case 3: line=board[0]+board[3]+board[6];
			break;
			case 4: line=board[1]+board[4]+board[7];
			break;
			case 5: line=board[2]+board[5]+board[8];
			break;
			case 6: line=board[0]+board[4]+board[8];
			break;
			case 7: line=board[2]+board[4]+board[6];
			break;
			}
		// FOR X WINNER
		if(line.equals("xxx"))
			{return "x";}
		// FOR 0 WINNER
		else if(line.equals("000"))
			{return "0";}	
	}
	
	for (int a=0;a<9;a++) 
	{
		if(Arrays.asList(board).contains(String.valueOf(a + 1)))
		{ break;}
		else if(a ==8) {
			return "draw";
			}
	}
	System.out.println( turn + "'s turn; enter a slot number to place " + turn + " in:");
	return null;
	}
	
	//xoxo board display
	static void displayBoard()//printBoard
	{
		System.out.println("|---|---|---|");
		System.out.println("| " + board[0] + " | " + board[1] + " | " + board[2] + " | ");
		System.out.println("|---|---|---|");
		System.out.println("| " + board[3] + " | " + board[4] + " | " + board[5] + " | ");
		System.out.println("|---|---|---|");
		System.out.println("| " + board[6] + " | " + board[7] + " | " + board[8] + " | ");
		System.out.println("|---|---|---|");
	}
	
	public static void main(String[] args) {
		// TODO Auto-generated method stub
		Scanner in = new Scanner(System.in);
		board = new String[9];
		turn = "x";
		String winner = null;
		for(int a=0;a<9;a++)
		{
			board[a]=String.valueOf(a + 1);
		}
		System.out.println("Welcome to 3x3 Tic Tac Toe.");
		displayBoard();
		System.out.println("x will play first, Enter a slot number to place");
		while(winner == null) {
			int input;//numInput
			try {
				input = in.nextInt();
				if(!(input>0 && input<=9))
				{
					System.out.println("invalid input,re-enter slot number:");
				continue;
				}
			}
			catch(InputMismatchException e) {
				System.out.println("invalid innput,re-enter slot number:");
			continue;
			}
			if(board[input -1].equals(String.valueOf(input)))
			{
				board[input -1]=turn;
				if(turn.equals("x")) {
					turn="0";
					}
				else {
				turn="x";
					}
			displayBoard();
			winner = alotWinner();
			}
			else {
				System.out.println("slot full, try next slot");
			}
		}
		if(winner.equalsIgnoreCase("draw"))
			{
			System.out.println("It's a draw!Thanks for playing");
			}
		else {
			System.out.println("YAAY" + winner + " 's have won!");
			System.out.println("lets try once again");
		}
		in.close();
	}
}

