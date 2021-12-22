# CRUD-StudentDB
 to implement the CRUD  i.e create / read /update / delete students data from Student table.

1)Insert data into student table
package javaproject;

import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.SQLException;
import java.sql.Statement;


public class StudentsInsert {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
        String jdbcURL ="jdbc:mysql://localhost:3306/studentdb";
        String username	= "root";
        String password ="Atkar@2021";  
        try { 
        Connection Connection = DriverManager.getConnection(jdbcURL, username, password);
        Statement statment = Connection.createStatement();
        {
        String sql = "INSERT INTO student (student_name,student_DOB,student_DOJ)"
      		    + "VALUES ('Rashmi','1994-05-15','2019-12-22')";
            statment.executeUpdate(sql);

           sql = "INSERT INTO student (student_name,student_DOB,student_DOJ)"
      		    + "VALUES ('Harshu','1994-006-11','2021-04-06')";
            statment.executeUpdate(sql);

            sql = "INSERT INTO student (student_name,student_DOB,student_DOJ)"
                         + "VALUES ('Shraddha','1994-05-15','2021-12-08')";
           statment.executeUpdate(sql);
       
          
            sql = "INSERT INTO student (student_name,student_DOB,student_DOJ)"
            	      		    + "VALUES ('Dhiraj','1994-05-15','2019-12-22')";
            statment.executeUpdate(sql);
         {
        	System.out.println("A new Student has been inserted successfully");
        	
        }
        Connection.close();         
        
        }catch(SQLException ex) {
        	ex.printStackTrace();
        }
	
	}
}


output: A new Student has been inserted successfully
 
     student_name       student_DOB	student_DOJ
1	Rashmi  	1994-05-15	2019-12-22
2	Harshu  	1994-06-11	2021-04-06
3	Shraddha        1994-05-15	2021-12-08
4	Dhiraj	        1994-05-15	2019-12-22

2) Update student data into Student table

package javaproject;

import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.PreparedStatement;
import java.sql.SQLException;

public class StudentsUpdate {

	public static void main(String[] args) {
		// TODO Auto-generated method stub

		 String jdbcURL ="jdbc:mysql://localhost:3306/studentdb";
	        String username	= "root";
	        String password ="Atkar@2021";
	      
	        
	        String student_DOB = "1995-04-23";
	        String student_DOJ = "2020-12-22";
	        String student_name = "Harshu";

	        
	        try {
	        Connection Connection = DriverManager.getConnection(jdbcURL, username, password);
	        
	        //Updating database
            String sql1 = "UPDATE student SET student_DOB =?, student_DOJ=? WHERE student_name =?";
            
            PreparedStatement statment = Connection.prepareStatement(sql1);
          
            statment.setString(1, student_DOB);
            statment.setString(2, student_DOJ);
            statment.setString(3, student_name);

            
            int rows1 = statment.executeUpdate();
            
            if(rows1 > 0) {
            	System.out.println("Information has been updated successfully");
            	
            }
            Connection.close();         
            
            }catch(SQLException ex) {
            	ex.printStackTrace();
            }
    	
	}

}

OUTPUT:- Information has been updated successfully
	
            student_name  student_DOB	student_DOJ		
	1	Rashmi	1994-05-15	2019-12-22
	2	Harshu	1995-04-23	2020-12-22
	3	Shraddha 1994-05-15	2021-12-08
	4	Dhiraj	1994-05-15	2019-12-22

3) Delete student data from Student table

package javaproject;

import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.PreparedStatement;
import java.sql.SQLException;

public class StudentDelete {

	public static void main(String[] args) {
		// TODO Auto-generated method stub

		 String jdbcURL ="jdbc:mysql://localhost:3306/studentdb";
	        String username	= "root";
	        String password ="Atkar@2021";
	        
	        String student_name = "Harshu";

	        try {
		        Connection Connection = DriverManager.getConnection(jdbcURL, username, password);
		        
	            String sql1 = "DELETE From student WHERE student_name =?";
	            PreparedStatement statment = Connection.prepareStatement(sql1);
	            statment.setString(1, student_name);

	            
	            int rows1 = statment.executeUpdate();
	            
	            if(rows1 > 0) {
	            	System.out.println("Information has been Deleted successfully");
	            	
	            }
	            Connection.close();         
	            
	            }catch(SQLException ex) {
	            	ex.printStackTrace();
	            
      	}

	}

}

OUTPUT:   Information has been Deleted successfully

            student_name  student_DOB	student_DOJ
	1	Rashmi	1994-05-15	2019-12-22
	2	Shraddha 1994-05-15	2021-12-08
	3	Dhiraj	1994-05-15	2019-12-22



4)4. Get a list of all students.

package javaproject;

import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.PreparedStatement;
import java.sql.ResultSet;
import java.sql.SQLException;

public class GetList {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		
		String jdbcURL ="jdbc:mysql://localhost:3306/studentdb";
        String username	= "root";
        String password ="Atkar@2021";
     

        try {
	        Connection Connection = DriverManager.getConnection(jdbcURL, username, password);
	        
            String sql1 = "SELECT * From student";
            PreparedStatement statment = Connection.prepareStatement(sql1);

           ResultSet rs = statment.executeQuery(sql1);
            
            if(rs.next()) {
            	System.out.println("Get A List Of All Students successfully");
            	
            } 
            Connection.close();         
             }catch(SQLException ex) {
        	ex.printStackTrace();

         }
	}
}

OUTPUT: Get A List Of All Students successfully
   
            student_name  student_DOB	student_DOJ
	1	Rashmi	1994-05-15	2019-12-22
	2	Shraddha 1994-05-15	2021-12-08
	3	Dhiraj	1994-05-15	2019-12-22

5) Get one student information depending on the student id filter.

package javaproject;

import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.PreparedStatement;
import java.sql.ResultSet;
import java.sql.SQLException;

public class GetStudentInfo {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		String jdbcURL ="jdbc:mysql://localhost:3306/studentdb";
        String username	= "root";
        String password ="Atkar@2021";
     

        try {
	        Connection Connection = DriverManager.getConnection(jdbcURL, username, password);
	        
            String sql1 = "SELECT student_name,student_DOB,student_DOJ From student WHERE student_no ='1'";
            PreparedStatement statment = Connection.prepareStatement(sql1);

           ResultSet rs = statment.executeQuery(sql1);
            
            if(rs.next()) {
            	System.out.println("Get A List Of One Students successfully");
            	
            } 
            Connection.close();         
             }catch(SQLException ex) {
        	ex.printStackTrace();

         }
	}
}


OUTPUT:  Get A List Of One Students successfully

	student_name	student_DOB	student_DOJ
	Shilpa	1994-05-15	2019-12-22

