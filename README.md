# First_Project
import java.sql.Connection; 
import java.sql.DriverManager; 
import java.sql.PreparedStatement; 
import java.sql.ResultSet; 
import java.sql.Statement; 
import java.util.Scanner; 
 
public class PlayerMiniProject { 
 static Scanner sc; 
 public static void main(String[] args) { 
  int opt=0; 
  sc = new Scanner(System.in); 
  do { 
   System.out.println("1. Add a new Player"); 
   System.out.println("2. Show all players "); 
   System.out.println("3. Update the player details "); 
   System.out.println("4. Delete any palyer"); 
   System.out.println("5. Exit "); 
   System.out.println("Enter your option "); 
   opt = sc.nextInt(); 
   switch(opt) { 
   case 1:addPlayer(); 
     break; 
   case 2:showPlayers(); 
     break; 
   case 3: updatePlayer(); 
     break; 
   case 4: deletePlayer(); 
     break; 
   case 5:break; 
   default:System.out.println("Invalid option "); 
   } 
  }while(opt!=5); 
 } 
 
 private static void deletePlayer() { 
  // TODO Auto-generated method stub 
   
 } 
 
 private static void updatePlayer() { 
  try { 
   //Step 1 Register the driver 
   Class.forName("com.mysql.cj.jdbc.Driver"); 
   //Step 2 Get Connection 
   Connection con = DriverManager.getConnection("jdbc:mysql://localhost:3306/jdbc","root","root"); 
   //System.out.println("Connection established"); 
   //Step 3 Create Statement 
   //Statement stmt = con.createStatement(); 
   String query = "update player set pname=? and country=? where pid=?"; 
   PreparedStatement pstmt = con.prepareStatement(query); 
   // Step 4 execute the query 
   System.out.println("Enter player id to update :"); 
   int x = sc.nextInt(); 
    
    
   System.out.println("Enter the new player name "); 
   String n = sc.next(); 
   System.out.println("Enter the new player country "); 
   String c = sc.next(); 
   pstmt.setString(1, n); 
   pstmt.setString(2, c); 
   pstmt.setInt(3, x); 
   int a = pstmt.executeUpdate(); 
   if(a>=1) 
    System.out.println(a+ " Record Updated Successfully "); 
   else 
    System.out.println("Record not found "); 
   //stmt.executeUpdate(query); 
 
   // Step 5 close the connection 
   con.close(); 
  } 
  catch(Exception e) { 
   System.out.println(e); 
  } 
   
   
 } 
 
 private static void showPlayers() { 
  // TODO Auto-generated method stub 
   
 } 
 
 private static void addPlayer() { 
  try { 
   //Step 1 Register the driver 
   Class.forName("com.mysql.cj.jdbc.Driver"); 
   //Step 2 Get Connection 
   Connection con = DriverManager.getConnection("jdbc:mysql://localhost:3306/jdbc","root","root"); 
   System.out.println("Connection established"); 
   //Step 3 Create Statement 
   //Statement stmt = con.createStatement(); 
   String query = "insert into player values(?,?,?)"; 
   PreparedStatement pstmt = con.prepareStatement(query); 
   // Step 4 execute the query 
   System.out.println("Enter player id "); 
   int x = sc.nextInt(); 
   sc.nextLine(); 
   System.out.println("Enter the player name "); 
   String n = sc.nextLine(); 
   System.out.println("Enter the player country "); 
   String c = sc.next(); 
   pstmt.setInt(1, x); 
   pstmt.setString(2, n); 
   pstmt.setString(3, c); 
   pstmt.executeUpdate(); 
   //String query = "insert into player values("+ x +",'"+n+"','"+c+"')"; 
   //System.out.println(query); 
   System.out.println("Record inserted"); 
   //stmt.executeUpdate(query); 
 
   // Step 5 close the connection 
   con.close(); 
  } 
  catch(Exception e) { 
   System.out.println(e); 
  } 
   
 } 
}
