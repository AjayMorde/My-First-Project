# My-First-Project
My First Project On ATM Machine


package MyFirstProject;
import java.util.Scanner;
import java.util.ArrayList;
class Person
{
	String name;
	int account_no;
	int balance;
	int PIN;
	
	public Person(String name,int account_no,int balance,int PIN)
	{
		this. name=name;
		this.account_no=account_no;
		this.balance=balance;
	    this.PIN=PIN;            
		
	}
	
}
class ATM {
	ArrayList<Person>account;
	public ATM (){
		account=new ArrayList<>();
	}
	private Person getPerson(String enter_name,int enter_account_no) {
		 Person p=null; 
		   for(int i=0;i<account.size();i++)
		   {
			   Person currPerson=account.get(i); 
			   if(currPerson.name.equals(enter_name)||currPerson.account_no==enter_account_no) {
				   p=currPerson; 
				   break;     
			   } 
		   } 
		  
		   return p;  
		 
	}

   public void	withdrawCash(Person p,int entered_PIN,int amount)  
{
	if(p.PIN== entered_PIN) 
	{	if(p.balance<amount) {
			System.out.println("This much money is not avialble in your account,Current balnce is " +p.balance);
		}
		else {
			p.balance=p.balance-amount;
			System.out.println("Amount received "+amount+ " The updated balance is "+p.balance);
		}
	
	}
	else 
	{
		System.out.println("OPPs! You Are Entered Wrong PIN");
	}
	
	
}
   public void	withdrawCash(String enter_name,int enter_account_no,int enter_PIN,int amount ) {
	  
	   Person p=getPerson(enter_name,enter_account_no);
	   if(p==null) {
		   System.out.println("There is no account with name "+enter_name+ "and account with "+enter_account_no);
	   }
	   withdrawCash( p, enter_PIN, amount) ; 
		  
	 }   
   public void depositeCash(Person p,int enter_amount)
{
	   p.balance=p.balance+enter_amount;
	   System.out.println("new balance is "+p.balance);
}

	   public void	depositeCash(String enter_name,int enter_account_no,int enter_PIN) {
		   Person p=getPerson(enter_name,enter_account_no);
		   
	   
	
	if(p==null) {
		   System.out.println("There is no account with name "+enter_name + "and account with "+enter_account_no);
		   
	   }
	   }
	
   public void getbalance(Person p,int enter_PIN) 
{
	if(p.PIN==enter_PIN) {
		System.out.println("The balance is "+p.balance);
	}
	else {
		System.out.println("OPPS Your Entered wronge PIN.Please try again");
	}
	 
	
}
   public void	getbalance(String enter_name,int enter_account_no,int enter_PIN,int amount ) {
	   
	   Person p=getPerson(enter_name,enter_account_no);
	   if(p==null)
	   {
		   System.out.println("There is no account with name "+enter_name + "and account with "+enter_account_no);
	   }
	   getbalance( p, enter_PIN) ;
	 }
   
   public void changePin(Person p,int Old_PIN,int New_PIN)
{
	   if(p.PIN==Old_PIN) {
			System.out.println("The PIN is changed");
		}
		else {
			System.out.println("OPPS Your Entered wronge old PIN.Please try again");
		}
}

	

}

public class Question {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		System.out.println(" ");
		Scanner sc=new Scanner(System.in);
		ATM bank=new ATM();
		
		Person p1=new Person("Ajay",1,100,4615);
		bank.account.add(p1);
		Person p2=new Person("Swapnil",2,1000,5555);
		bank.account.add(p2);
//		regester with atm
		
		
		bank.withdrawCash(p1,4615,50);
		bank.withdrawCash(p2,5555,500);
		bank.withdrawCash("Ajay",1,4615,700); 
		
		
		bank.depositeCash(p2, 100);
		bank.depositeCash("Ajay",1,4615);    
		
		bank.getbalance(p1, 4615);
		bank.getbalance(p2, 4258);
		bank.getbalance("Ajay",1,4615,50);
		
		
		bank.changePin(p1,4615,4000);
		bank.withdrawCash(p1,4615,70);
		
		
		
		  
		
		
		
		
		
		
		
		
		
		
		
		
		
		
		
		
		
		
	}

}

