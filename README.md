# CSE623-23704

package net.codejava;

import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.SQLException;
import java.sql.Statement;

public class ContactProgram {

	public static void main(String[] args) {
		String jdbcURL = "jdbc:postgresql://localhost:5432/postgres";
		String username = "postgres";
		String password = "admin";
		
		try {
			Connection connection = DriverManager.getConnection(jdbcURL, username, password);
			System.out.println("connected to Postgres");
			
			// 1. Delete product p1 from Product and Stock
			String sql = "DELETE FROM stock WHERE prodid = 'p1'";
			//String sql = "DELETE FROM product WHERE prodid = 'p1'";
			
			//3. Change product pl name to pp1 in Product and Stock
			//String sql = ("UPDATE product SET pname = 'pp1' WHERE prodid = 'p1'");
			//String sql = ("UPDATE stock SET pname = 'pp1' WHERE prodid = 'p1'");
			
			//5. Add product (p100, cd, 5) in Product and (p100, d2, 50) in Stock
			//String sql = ("INSERT INTO product (prodid, pname) VALUES ('p100', 'cd')");
			//String sql = ("INSERT INTO stock (prodid, depid, quantity) VALUES ('p100', 'd2', 50)");			
			
			
			Statement statement = connection.createStatement();
			
			int rows = statement.executeUpdate(sql);
			
			connection.close();
		} catch (SQLException e) {
			System.out.println("Error in connecting to Postgres");
			e.printStackTrace();
		}

	}

}
