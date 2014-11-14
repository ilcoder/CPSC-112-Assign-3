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

public static boolean isGameOver(String input) {
 
	  int x = 0;
	  int y = 0;
	  	
if(isGuessValid(input))
	  {
	  for (int k=0; k< 4; k++)
	  {
	     if(input.charAt(k)==mySecret.charAt(k))
	     {
	       y = y + 1;
	      }
	       }

	  for(int j = 0; j<4; j++)
	  {
	      for (int i=0; i< 4; i++){
	         if(input.charAt(i)==mySecret.charAt(j))
	            {
	              x = x + 1;
	                  }
	               }
	  }
	  int s = x;
	  int t = y;
	  int l=Integer.parseInt(input);
	  int e=Integer.parseInt(mySecret);
	  int p = r.nextInt(3) + 1;
	  int o = r.nextInt(2);

if(f % 2==0)
	  { 
	if(p==2){
	    f = f + 1;
	     if(o==0){
	    	 if(x==4 && y==4){
	       while (x < y || (x==4 && y==3) ||(x==4 && y==4)||y==t){
	          
	    	   y= r.nextInt(4); 
	    	  
	         }
	    	 } else{
	    		 while (x < y || (x==4 && y==3) ||(x==4 && y==4)||x==s){
	   	          
	  	    	   x= r.nextInt(5); 
	  	    	   
	  	         }
	    	 }
	         
	  }else {
	      while(x < y || (x==4 && y==4) || (x==4 && y==3) || y==t){
	      y = r.nextInt(5);
	      
	   }
	   }
	 if (DEBUG){
		 if(l==e && l>max){
				max=l;
			    System.out.println("Guess: " + input + "; " + "Result: " + x + "," + y);
			  }
			else if(l==e && l<max && c>=0){
				 System.out.println("Your guess was lower than allowed. You have " + c + " exceptions remaining.");
				 System.out.println("Guess: " + input + "; " + "Result: " + x + "," + y);
			  }
			else if(l==e && l<max && c<0){
				  System.out.println("Your guess was lower than allowed. You have " + 0 + " exceptions remaining.");
				  System.out.println("Guess: " + input + "; " + "Result: " + x + "," + y);
				  }
			else if(l>max && c>=0 && l!=e)
		  	 {
		  	 	max=l;
		  	    System.out.println("Guess: " + input + "; " + "Result: " + x + "," + y);
		  	    }
			  
			else if(l>max && c<0 && l<e)
			  	 {
			  	 	max=l;
			  	 System.out.println("Guess: " + input + "; " + "Result: " + x + "," + y);
			  	    }
			  
		    else if (l < max && c>=0 && l!=e) {
		  	 System.out.println("Your guess was lower than allowed. You have " + c + " exceptions remaining.");
		  	 System.out.println("Guess: " + input + "; " + "Result: " + x + "," + y);
		  	 c = c-1;
		  	 }
		  	 else if (l < max && c<0 && l<e) {
		  	 System.out.println("Your guess was lower than allowed. You have " + 0 + " exceptions remaining.");
		  	 System.out.println("Guess: " + input + "; " + "Result: " + x + "," + y);
		  	 }

		  	 else if (l > e && c<=0 && l>max)
		  	 {
		  	 	System.out.println("You're out of exceptions and you've guessed too high! The secret was " + mySecret);
		  	 }

		  	 else if (l > e && c<=0 && l<max)
		  	 {
		  	 	System.out.println("Your guess was lower than allowed. You have " + 0 + " exceptions remaining.");
		  	 	System.out.println("You're out of exceptions and you've guessed too high! The secret was " + mySecret);
		  	 }
		  
	  	 System.out.println("Lie.");
	  	 return true;
	  } else {
		  
		  if(l==e && l>max){
			  max=l;
			 System.out.println("Guess: " + input + "; " + "Result: " + x + "," + y);
		  }
		  else if(l==e && l<max && c>=0){
			 System.out.println("Your guess was lower than allowed. You have " + c + " exceptions remaining.");
			 System.out.println("Guess: " + input + "; " + "Result: " + x + "," + y);
		  }
		  else if(l==e && l<max && c<0){
			  System.out.println("Your guess was lower than allowed. You have " + 0 + " exceptions remaining.");
			  System.out.println("Guess: " + input + "; " + "Result: " + x + "," + y);
			  }
		   else if(l>max && c>=0 && l!=e)
	  	 {
	  	 	max=l;
	  	 System.out.println("Guess: " + input + "; " + "Result: " + x + "," + y);
	  	    }
		  
		   else if(l>max && c<0 && l<e)
		  	 {
		  	 	max=l;
		  	 System.out.println("Guess: " + input + "; " + "Result: " + x + "," + y);
		  	    }
		  
	  	 else if (l < max && c>=0 && l!=e) {
	  	 System.out.println("Your guess was lower than allowed. You have " + c + " exceptions remaining.");
	  	 System.out.println("Guess: " + input + "; " + "Result: " + x + "," + y);
	  	 c = c-1;
	  	 }
	  	 else if (l < max && c<0 && l<e) {
	  	 System.out.println("Your guess was lower than allowed. You have " + 0 + " exceptions remaining.");
	  	 System.out.println("Guess: " + input + "; " + "Result: " + x + "," + y);
	  	 }

	  	 else if (l > e && c<=0 && l>max)
	  	 {
	  	 	System.out.println("You're out of exceptions and you've guessed too high! The secret was " + mySecret);
	  	 }

	  	 else if (l > e && c<=0 && l<max)
	  	 {
	  	 	System.out.println("Your guess was lower than allowed. You have " + 0 + " exceptions remaining.");
	  	 	System.out.println("You're out of exceptions and you've guessed too high! The secret was " + mySecret);
	  	 }
	
	  	 return true;
	  } 
	    }  else 
	   {
	    	
	    	if (l==e){
		    	System.out.println("You won!");
		    }
		    	
		    else if(l>max && c>=0 && l!=e)
		  {
		  	max=l;
		  System.out.println("Guess: " + input + "; " + "Result: " + x + "," + y);
		     }
		    
		   else if(l>max && c<0 && l<e)
			  {
			  	max=l;
			  	
			  System.out.println("Guess: " + input + "; " + "Result: " + x + "," + y);
			 
			     }

		  else if (l < max && c>=0 && l!=e) {
		  System.out.println("Your guess was lower than allowed. You have " + c + " exceptions remaining.");
		  System.out.println("Guess: " + input + "; " + "Result: " + x + "," + y);
		  
		  c = c-1;
		  }
		  else if (l < max && c<=0 && l<e) {
		  System.out.println("Your guess was lower than allowed. You have " + 0 + " exceptions remaining.");
		  System.out.println("Guess: " + input + "; " + "Result: " + x + "," + y);
		  }

		  else if (l > e && c<=0 && l>max)
		  {
		  	System.out.println("You're out of exceptions and you've guessed too high! The secret was " + mySecret);
		  }

		  else if (l > e && c<=0 && l<max)
		  {
		  	System.out.println("Your guess was lower than allowed. You have " + 0 + " exceptions remaining.");
		  	System.out.println("You're out of exceptions and you've guessed too high! The secret was " + mySecret);
		  }
		
		     } return true;
	  } else 
	   {
		  f = f + 1;
		    if (l==e){
		    	System.out.println("You won!");
		    }
		    	
		    else if(l>max && c>=0 && l!=e)
		  {
		  	max=l;
		  	
		  System.out.println("Guess: " + input + "; " + "Result: " + x + "," + y);
		 
		     }
		    
		   else if(l>max && c<0 && l<e)
			  {
			  	max=l;
			  	
			  System.out.println("Guess: " + input + "; " + "Result: " + x + "," + y);
			 
			     }

		  else if (l < max && c>=0 && l!=e) {
		  System.out.println("Your guess was lower than allowed. You have " + c + " exceptions remaining.");
		  System.out.println("Guess: " + input + "; " + "Result: " + x + "," + y);
		  c = c-1;
		  }
		  else if (l < max && c<=0 && l<e) {
		  System.out.println("Your guess was lower than allowed. You have " + 0 + " exceptions remaining.");
		  System.out.println("Guess: " + input + "; " + "Result: " + x + "," + y);
		  }

		  else if (l > e && c<=0 && l>max)
		  {
		  	System.out.println("You're out of exceptions and you've guessed too high! The secret was " + mySecret);
		  }

		  else if (l > e && c<=0 && l<max)
		  {
		  	System.out.println("Your guess was lower than allowed. You have " + 0 + " exceptions remaining.");
		  	System.out.println("You're out of exceptions and you've guessed too high! The secret was " + mySecret);
		  }
		 
		     } return true;
	  }
	    
	  return false;
	  
  }
}

