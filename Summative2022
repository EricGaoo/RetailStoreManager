//=================================================================
// Program name: Summative2022
// Author: Eric Gao
// Date: January 25, 2021
// Programming Language: Eclipse IDE for Java Developers
// Version: Neon.1a Release (4.6.1)
// Build id: 20161007-1200
//=================================================================
//Problem Definition – required to create a retail store program 
//I - input of user’s login details, user's program choice and various inputs to run each of the 3 programs
//O - outputs the same 3 programs
//P - There will first be a login page. Users will input there username and password to identify if they are employees or managers. 
//	  is prompted to continue or choose a new program. If they select to continue, the program will 
//	  repeat. If they select to stop, they will choose a new program.
//	  
//
//
//=================================================================
/*List of Variables 
*see documentation below
*/

import java.io.*;

public class Summative2022 {
	
	public static void main(String[] args) throws IOException{
	
	boolean userVerify = false, passVerify = false, finished = false, integerCheck = false; //these variables are used to verify with boolean. and to indicate if a loop should be run again
	String username, password, rerun; //these strings represent relevant user string input
	int invoiceNum = 0,passIndex = 0, categoryInput = 0, productInput, productCount = 0, shiftsCount = 0, day, employeeChoice = 0, startTime, endTime; //these int variables are used as accumalators in for loops which are used in for various indices in arrays
	final double HSTAMOUNT = 0.13, HSTFINAL = 1.13, MINWAGE = 15; //constants for calculation
	double fullTotal = 0, iphoneTotal = 0, macbookTotal = 0, imacTotal = 0, airpodsTotal = 0, ipadTotal = 0, dailyTotal = 0, HST, tax; //these doubles hold and accumalate total and subtotal values
	double iphoneValues [] = {1200, 1600, 2100}; // array of different prices in the iphone category
	double macbookValues [] = {1300, 2300, 3500}; //array of different priced in the macbook category
	double imacValues [] = {799, 1000, 1600}; //array of different priced in the imac category
	double airpodsValues [] = {200, 550, 899}; //array of different priced in the aipds category
	double ipadValues [] = {1400, 1900, 2700}; //array of different priced in the ipad category
	double totals[] = {0, 0, 0, 0, 0, 0}; //array of total sales in each category for subtotal
	double categoryTotals[] = {0,0,0,0,0, 0}; //array of total sales of products in each category
	double Totals[] = {0,0,0,0,0}; //array of different priced in the macbook category
	double employeeHours[][] = {{0,0,0,0,0}, {0, 0, 0, 0, 0, 0}}; //array of different priced in the macbook category
	double employeePay[] = {0,0,0,0,0}; //array of different priced in the macbook category
	int shifts[][][] = new int[7][16][2]; //array of different priced in the macbook category
	
	String loginDatabase[][] = {
				{"Eric", "Dominic", "Hrushi", "Andy", "Marcus", "Mr.K"}, {"red", "blue", "green", "yellow", "orange", "purple"}
	};	
		
	Summative2022 retailSoftware = new Summative2022();
	
	System.out.println("WELCOME TO THE APPLE STORE RETAIL SYSTEM ");
	System.out.println("Login: ");
	
	System.out.println("Input your username: ");
	username = retailSoftware.stringInput();
	
	do { // do while loop
		for (int i = 0; i < 6; i++) { //for loop. This loop basically compares username input to each of the indexes in the array.
			if (username.equals(loginDatabase[0][i])) {
				userVerify = true; //if it detects a match, the username is verified and the loop will not rerun for username input
				if (userVerify == true) {
					username = loginDatabase[0][i]; //when it matches, it will also store the username
					passIndex = i; //this is important. When it fins it match, the loop holds the index which will be used to find the corresponding password
				}
			}
		}
		if (userVerify == false) { //if there isn't a match, the user is promopted with this to re-enter their username
			System.out.println("Invalid username! Please enter again: ");
			System.out.println("Input your username: ");
			username = retailSoftware.stringInput();
		}
	}while(userVerify == false); //exit condition
	
	System.out.println("Input your password: ");
	password = retailSoftware.stringInput();
	
	do { //do while loop
		if (password.equals(loginDatabase[1][passIndex])) { //with the matching password index, it compares the password in the array with the user input. 
			passVerify = true; //if there is a match then the user exits the loop and can start the program
		}
		else {
			if (passVerify == false) { //if there is no match, the user must re-enter a valid password
				System.out.println("Incorrect! Please enter again: ");
				System.out.println("Input your password: ");
				password = retailSoftware.stringInput();
			}
		}

	}while(passVerify == false); //exit condition
	
	System.out.println("Welcome "+username);
	
	do { //do while loop
		System.out.println("Please choose from the software functions below: ");
		if (username.equals(loginDatabase[0][5])) { // if statement here to show the manager functions if you are the manager. It just matches the stored username with the manager username in the array
			retailSoftware.part1Menu();
			retailSoftware.part2Menu();
			retailSoftware.part3Menu();
		}
		else { //employee functions here
			retailSoftware.part1Menu();
		}
		do {
			try { // try catch for determining a valid choice in the selection of programs. This makes sure user can't input a string
				employeeChoice = retailSoftware.intInput();
				if (employeeChoice <1 || employeeChoice > 3) { //parameters set to 1 and 3 which are the 3 programs to choose
					integerCheck = false; //a boolean variable to verify if the input is valid to exit/loop
					System.out.println("please input a valid choice");
				}
				else
					integerCheck = true;
		}
		catch (NumberFormatException error) {
			System.out.println("please input a valid choice");
			integerCheck = false;
		}
		}while (integerCheck == false);
		
	}while (!(employeeChoice == 1||(employeeChoice == 2 && username.equals("Mr.K"))||(employeeChoice == 3 && username.equals("Mr.K"))));{ //one final condition to make sure you cannot use manager functions if you are an employee
	
	
		if (employeeChoice == 1) {
			do {
				retailSoftware.itemMenu(); //showing the product and categories
				System.out.println("Welcome to the Daily Sale Program!");
				System.out.println("Please input the customer category? Or input 123 when you are finished"); //prompt for which category
				do {
					try { //try and catch to make sure user isn't inputting a string or a invalid category
						categoryInput = retailSoftware.intInput();
						if (categoryInput <1 || categoryInput > 5) { //parameters set to 1 and 5 which are the 5 categories to choose
							integerCheck = false;
							System.out.println("please input a valid choice");
						}
						else
							integerCheck = true;
				}
				catch (NumberFormatException error) {
					System.out.println("please input a valid choice");
					integerCheck = false;
				}
				}while (integerCheck == false); // while loop for try and catch
				
				while (!(categoryInput == 123)){
					System.out.println("Please input the customer product?"); //prompt for the product in the category
					productInput = retailSoftware.intInput();
					System.out.println("Please input the customer how many the customer bought?"); //prompt for the # of products
					productCount = retailSoftware.intInput();
					
					//below is Used selection based on category to choose the corresponding array with the prices. Then, I use the user input to find the index of the correct price and multiply it with the # of products. I store it in an array for subtotals
					//I use categoryTotals later to find the full amount sold since totals[] is reset when the loop runs again to accuratly get the price of the next customer
					if (categoryInput == 1) {
						totals[0] += productCount*(iphoneValues[productInput-1]);	
						categoryTotals[0] += totals[0];
					}
					else if (categoryInput == 2) {
						totals[1] += productCount*(macbookValues[productInput-1]);
						categoryTotals[1] += totals[1];
						
					}
					else if (categoryInput == 3) {
						totals[2] += productCount*(imacValues[productInput-1]);
						categoryTotals[2] += totals[2];
					}
					else if (categoryInput == 4) {
						totals[3] += productCount*(airpodsValues[productInput-1]);
						categoryTotals[3] += totals[3];
					}
					else if (categoryInput == 5) {
						totals[4] += productCount*(ipadValues[productInput-1]);
						categoryTotals[4] += totals[4];
					}	
					
					System.out.println("Please input the customer category? Or input 123 when you are finished");
					categoryInput = retailSoftware.intInput();
					
				}
				
				for (int i = 0; i < 4; i++) { //this is a for loop to compare and find the highest category sales in the system.
					if (categoryTotals[i] < categoryTotals[i+1] ) {
						categoryTotals[5] = categoryTotals[i+1]; 
					}
				}
				
				for (int j = 0; j < 4; j++) { //here I use a for loop to reset all totals[] back to 0 for the net customer order
					fullTotal = fullTotal + totals[j];
				}
				
				HST = fullTotal*HSTFINAL; //calculating the amount of HST
				tax = fullTotal*HSTAMOUNT; //calculating the full total with HST
				
				invoiceNum += 1; //an invoice number creator
				
				//full receipt below
				System.out.println("Receipt");
				System.out.println("salesman: "+username);
				System.out.println("#"+invoiceNum);
				System.out.println("iPhone subtotals: "+totals[0]);
				System.out.println("Macbook subtotals: "+totals[1]);
				System.out.println("iMac subtotals: "+totals[2]);
				System.out.println("Airpods subtotals: "+totals[3]);
				System.out.println("iPad subtotals: "+totals[4]);
				System.out.println("Subtotal: "+fullTotal);
				if (username.equals("Eric")) { //here, I use selection to accumalate sales for each employee based on their input I use an index of an array to store each sale
					employeePay[0] += fullTotal;
				}
				else if (username.equals("Dominic")) {
					employeePay[1] += fullTotal;
				}
				else if (username.equals("Hrushi")) {
					employeePay[2] += fullTotal;
				}
				else if (username.equals("Andy")) {
					employeePay[3] += fullTotal;
				}
				else if (username.equals("Marcus")) {
					employeePay[4] += fullTotal;
				}
				System.out.println("Tax: "+tax);
				System.out.println("Total: "+HST);
				
				for (int k = 0; k < 4; k++) {
					totals[k] = 0;
				}
				dailyTotal += fullTotal; //daily total accumalator to find out sales for the day 
				fullTotal = 0; //resetting variables back to zero for accurate numbers in the next customer order
				tax = 0;
				HST = 0;
				
				System.out.println("Would you like to enter another order?");
				rerun = retailSoftware.stringInput();
				
			}while(!(rerun.equals("no")));
		}
	}
	
	

	if (employeeChoice == 2) { // regular manager program
		System.out.println("Welcome to manager program!");
		System.out.println("Choose from the following functions below:");
		retailSoftware.part2SubMenu();
		employeeChoice = retailSoftware.intInput();
		
		if (employeeChoice == 1) {
			do {
				System.out.println("Which week?"); //I have a 3 dimensional array that stores the 
				day = retailSoftware.intInput();

				System.out.println("Shifts: ");
				for (int l = 7; l < 19; l++) {
					shiftsCount += 1;
					shifts[day][shiftsCount][0] = l;
					if (l > 12) {
						shifts[day][shiftsCount][0] = shifts[day][shiftsCount][0] - 12;
					}
					System.out.println(shifts[day][shiftsCount][0]+":00 --> ");
				}
				System.out.println("Would you like to edit a shift?");
				rerun = retailSoftware.stringInput();
				
				while(!(rerun.equals("no"))) {
					System.out.println("Which employee is working: ");
					retailSoftware.employeeList();
					employeeChoice = retailSoftware.intInput();
					System.out.println("When does their shift start: ");
					startTime = retailSoftware.intInput();
					System.out.println("When does their shift end: ");
					endTime = retailSoftware.intInput();

					if (startTime < 6 || endTime < 6) {
						startTime += 12;
						endTime += 12;
					}

					for (int m = startTime; m < endTime; m++) {
						shifts[day][m-6][1] = employeeChoice;
					}

					for (int l = 1; l < 13; l++) {
						System.out.print(shifts[day][l][0]+":00 --> ");
						if (shifts[day][l][1] == 1) {
							System.out.println("Eric");
						}
						else if (shifts[day][l][1] == 2) {
							System.out.println("Dominic");
						}
						else if (shifts[day][l][1] == 3) {
							System.out.println("Hrushi");
						}
						else if (shifts[day][l][1] == 4) {
							System.out.println("Andy");
						}
						else if (shifts[day][l][1] == 5) {
							System.out.println("Marcus");
						}
						else if (shifts[day][l][1] == 6) {
							System.out.println("Mr.K");
						}
						else {
							System.out.println("("+shifts[day][l][1]+")");
						}
						
							
					}
					System.out.println("Would you like to enter any more shifts?");
					rerun = retailSoftware.stringInput();

				}
				System.out.println("Would you like to enter choose a new week?");
				rerun = retailSoftware.stringInput();
				shiftsCount = 0;
			}while(!(rerun.equals("no")));

				System.out.println("Weekly Pay");
				
				for (int m = 1; m < 7; m++) {
					for (int l = 1; l < 13; l++) {
						if (shifts[m][l][1] == 1) {
							employeeHours[0][1] += 1;
						}
						else if (shifts[m][l][1] == 2) {
							employeeHours[0][2] += 1;
						}
						else if (shifts[m][l][1] == 3) {
							employeeHours[0][3] += 1;
						}
						else if (shifts[m][l][1] == 4) {
							employeeHours[0][4] += 1;
						}
						else if (shifts[m][l][1] == 5) {
							employeeHours[0][5] += 1;
						}
					}

				for (int n = 1; n < 5; n++) {
					employeeHours[1][n] = MINWAGE*employeeHours[0][n];
				}
		}

			}
			
			if (employeeChoice == 2) {
				System.out.println("Employee pay: ");
				System.out.println("Eric pay: $"+employeeHours[1][1]);
				System.out.println("Dominic pay: $"+employeeHours[1][2]);
				System.out.println("Hrushi pay: $"+employeeHours[1][3]);
				System.out.println("Andy pay: $"+employeeHours[1][4]);
				System.out.println("Marcus pay: $"+employeeHours[1][5]);
			}
			if (employeeChoice == 3) {
				retailSoftware.itemMenu();
				System.out.println("Which category to change?");
				categoryInput = retailSoftware.intInput();
				System.out.println("Which product to change?");
				productInput = retailSoftware.intInput();
				System.out.println("What new price?");
				
				if (categoryInput == 1) {
					iphoneValues[productInput - 1] = retailSoftware.intInput();	
				}
				else if (categoryInput == 2) {
					macbookValues[productInput - 1] = retailSoftware.intInput();	
				}
				else if (categoryInput == 3) {
					imacValues[productInput - 1] = retailSoftware.intInput();	
				}
				else if (categoryInput == 4) {
					airpodsValues[productInput - 1] = retailSoftware.intInput();	
				}
				else if (categoryInput == 5) {
					ipadValues[productInput - 1] = retailSoftware.intInput();	
				}	
			}
	}

	
	if (employeeChoice == 3) {
		System.out.println("Total sales for the day: "+ dailyTotal);
		System.out.println("Total sales for the category: "+ categoryTotals[5]);
		System.out.println("Employee Sales: ");
		System.out.println("Eric's Sales: $"+employeePay[0]);
		System.out.println("Dominic's Sales: $"+employeePay[1]);
		System.out.println("Hrushi's Sales: $"+employeePay[2]);
		System.out.println("Andy's Sales: $"+employeePay[3]);
		System.out.println("Marcus's Sales: $"+employeePay[4]);
		System.out.println("Employee Hours: ");
		System.out.println("Eric pay: "+employeeHours[1][1]/MINWAGE);
		System.out.println("Dominic pay: "+employeeHours[1][2]/MINWAGE);
		System.out.println("Hrushi pay: "+employeeHours[1][3]/MINWAGE);
		System.out.println("Andy pay: "+employeeHours[1][4]/MINWAGE);
		System.out.println("Marcus pay: "+employeeHours[1][5]/MINWAGE);
		
	}
	
	}

	
	public void itemMenu() {
		/**itemMenu method:
		* This procedural method prints the menu of all the products and categories
		*/
		System.out.println("1 - iPhones");
		System.out.println("	1 - iPhone");
		System.out.println("	2 - iPhone Pro");
		System.out.println("	3 - iPhone Max");
		System.out.println("2 - Macbook");
		System.out.println("	1 - Macbook Air");
		System.out.println("	2 - Macbook");
		System.out.println("	3 - Macbook Pro");
		System.out.println("3 - iMac");
		System.out.println("	1 - iMac mini");
		System.out.println("	2 - iMac");
		System.out.println("	2 - iMac Pro");
		System.out.println("4 - Airpods");
		System.out.println("	1 - Airpods");
		System.out.println("	2 - Airpods Pro");
		System.out.println("	3 - Airpods Max");
		System.out.println("5 - IPad");
		System.out.println("	1 - iPad Air");
		System.out.println("	2 - iPad Air");
		System.out.println("	3 - iPad Pro");
		System.out.println("Input the number for the category, the number for the product and number of the product, input 'end' when you are done inputting products");
	}
	public void part1Menu() {
		/**paert1Menu method:
		* This procedural method prints the choice of part 1 and it;s functions
		*/
		System.out.println("1 - Daily Sales Functions - input customer purchases and get a receipt!");
		System.out.println("-------------------------------------------------");
	}
	public void part2Menu() {
		/**paert2Menu method:
		* This procedural method prints the choice of part 2 and it;s functions
		*/
		System.out.println("2 - Regular Management Functions - employee shifts, weekly pay, update specials and prices, call up sales");
		System.out.println("-------------------------------------------------");
	}
	public void part2SubMenu() {
		/**paert2SubMenu method:
		* This procedural method prints the sub choices of part 2 and it;s functions
		*/
		System.out.println("1 - See and Manage shifts");
		System.out.println("2 - View Weekly pay");
		System.out.println("3 - Update Specials and Prices");
		System.out.println("4 - View sale from invoice number");
	}
	public void part3Menu() {
		/**paert3SubMenu method:
		* This procedural method prints the choices of part 3 and it;s functions
		*/
		System.out.println("3 - Management Functions - see total sales, highest sales display, total sales for weeks, total sales from employee, hours and total HST!");
		System.out.println("-------------------------------------------------");
	}
	public void part3SubMenu() {
		/**paert3SubMenu method:
		* This procedural method prints the sub choices of part 3 and it's functions
		*/
		System.out.println("1 - See total sales");
		System.out.println("2 - Highest Sales");
		System.out.println("3 - Total sales by employee");
		System.out.println("4 - See total employee hours");
		System.out.println("5 - Financial Information");
		System.out.println("6 - add/remove employees");
	}
	
	public void employeeList() {
		/**employeeList method:
		* This procedural method prints the employees of the store
		*/
		System.out.println("1 - Eric");
		System.out.println("2 - Dominic");
		System.out.println("3 - Hrushi");
		System.out.println("4 - Andy");
		System.out.println("5 - Marcus");
		System.out.println("6 - Mr.K");
	}
	public String stringInput() throws IOException{

		/**stringInput method:
		* This functional method reads user string input, and returns the value
		*
		* List of Local Variables
		* br - a BufferedReader object used for keyboard input <type BufferedReader>;
		*
		* @param none
		* @throws IO Exception
		* @return the number input by user <type String>;
		*/
		
		BufferedReader br = new BufferedReader (new InputStreamReader(System.in));
		return br.readLine();
		
	}
	
	
	public int intInput() throws IOException{

		/**intInput method:
		* This functional method reads user integer input, and returns the value
		*
		* List of Local Variables
		* br - a BufferedReader object used for keyboard input <type BufferedReader>;
		*
		* @param none
		* @throws IO Exception
		* @return the number input by user <type int>;
		*/
		
		BufferedReader br = new BufferedReader (new InputStreamReader(System.in));
		return Integer.parseInt(br.readLine());
		
	}
	public double dblInput() throws IOException{

		/**dblinput method:
		* This functional method reads user double input, and returns the value
		*
		* List of Local Variables
		* br - a BufferedReader object used for keyboard input <type BufferedReader>;
		*
		* @param none
		* @throws IO Exception
		* @return the number input by user <type double>;
		*/
		
		BufferedReader br = new BufferedReader (new InputStreamReader(System.in));
		return Double.parseDouble(br.readLine());
		
	}

}
