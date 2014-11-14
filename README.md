CPSC-112-Assign-3
=================

package edu.yale.cpsc112_assignment3;

import java.util.Random;

public class CPSC112_Assignment3 {

  public static String mySecret = "";
  public static boolean DEBUG = true;
  public static Random r = new Random();
  public static int max = 0;
  public static int c = 2;	
  public static int f = 2;

  public static void main(String[] args) {
    makeMySecret();
    isGameOver("1234");
    isGameOver("4321");
    isGameOver("2567");
    isGameOver("1432");
  }

public static void makeMySecret() {
 
int w = r.nextInt(7) + 1, x = r.nextInt(7) + 1; 
int y = r.nextInt(7) + 1, z = r.nextInt(7) + 1;
		 
		 while(w==x || w==y || w==z)
		 {
			 w = r.nextInt(7) + 1;
		 }
		 
		 while(x==y || x==z || x==w)
		 {
			 x = r.nextInt(7) + 1;
		 }

		 while(y==x || y==z || y==w)
		 {
			 y = r.nextInt(7) + 1;
		 }

		 while(z==x || z==y || z==w)
		 {
			 z = r.nextInt(7) + 1;
		 }
		
		 mySecret = mySecret + x + y + z + w;
	  
    if (DEBUG)
    {
       System.out.println(mySecret);
    }
  }
  
  public static boolean isGuessValid(String input) {

	  if(input.length() != 4)
	  {
	  	System.out.println("Input must be a 4-digit number with digits between 1 and 7.");
	  	return false;
	  	
	  } else if (input.charAt(0)==input.charAt(1) || input.charAt(0)==input.charAt(2) ||
	  		input.charAt(0)==input.charAt(3) || input.charAt(1)==input.charAt(2) ||
	  		input.charAt(1)==input.charAt(3) || input.charAt(2)==input.charAt(3)) 
	  {
	  	System.out.println("Input must be a 4-digit number with digits between 1 and 7.");
	  	return false;
	  } 
	  else if (input.length() == 4) {
	  	try 
	  	{
	  		int i = Integer.parseInt(input);
	  		
	  	} catch(NumberFormatException nfe)
	  	{
	  		System.out.println("Input must be a 4-digit number with digits between 1 and 7.");
	  		return false;
	  	}
	  }
	  return true;
	  }

