# amend

package parser;

import java.util.List;
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.PreparedStatement;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;

import java.util.Iterator;

public class InsertDataInToDB {

	public static void insertData(List<Vehicle> listVehicle)
			throws SQLException, ClassNotFoundException {
		Vehicle v = null;
		try {
			int updateRecord = 0;
			int insertRecord = 0;
			int count = 0;
			Class.forName("oracle.jdbc.driver.OracleDriver");
			Connection con = DriverManager.getConnection(
					"jdbc:oracle:thin:@192.168.2.86:1521:orcl", "rainbow",
					"rainbow");

			Statement statement = con.createStatement();

// ===================================================================================================================================================================================================================================================================================================================================================
			String insertQuery = "insert into TABLE_TEST  (ID,LINE_CODE,PART_NUMBER,DESCRIPTION,COST_PRICE,LIST_PRICE,UPC,QUANTITY,LOCATION,DISTRIBUTOR_ID) values(?,?,?,?,?,?,?,?,?,?)";
// ======================================================================================================================================================================================
			PreparedStatement psmt = null;

			Iterator<Vehicle> iterator = listVehicle.iterator();
			int maxId = 0;
			while (iterator.hasNext()) {
				v = (Vehicle) iterator.next();

				String selectQuery = "select ID from TABLE_TEST where LINE_CODE='"
						+ v.getLineCode()
						+ "' and PART_NUMBER='"
						+ v.getPartNumber()
						+ "' and LOCATION="
						+ v.getLocation()
						+ " and DISTRIBUTOR_ID="
						+ v.getDistributerId() + " ";
				System.out.println(selectQuery);
				ResultSet resultSet = statement.executeQuery(selectQuery);

				try {
					if (resultSet.next()) {
//===========================================================================================================================================
						//Record Update Code//
//===========================================================================================================================================
						String updateQuery = "UPDATE TABLE_TEST SET  LINE_CODE=? , PART_NUMBER=? ,DESCRIPTION=?,COST_PRICE=?,LIST_PRICE=?, UPC=?,QUANTITY=?,LOCATION=?,DISTRIBUTOR_ID=?  WHERE ID=? ";
						psmt = con.prepareStatement(updateQuery);
						psmt.setString(1, v.getLineCode());
						psmt.setString(2, v.getPartNumber());
						psmt.setString(3, v.getDescription());
						psmt.setDouble(4, v.getCostPrice());
						psmt.setDouble(5, v.getListPrice());
						psmt.setString(6, v.getUpc());
						psmt.setString(7, v.getQuantity());
						psmt.setInt(8, v.getLocation());
						psmt.setInt(9, v.getDistributerId());
						psmt.setInt(10, resultSet.getInt("ID"));
						psmt.execute();

						System.out.println("Updeted Query=====>"
								+ updateRecord++);

					}

					else {
//===========================================================================================================================================
						//Record Insertion Code//
//===========================================================================================================================================
						System.out
								.println("select MAX(ID) from TABLE_TEST where DISTRIBUTOR_ID="
										+ v.getDistributerId() + "");
						ResultSet rs = statement
								.executeQuery("select MAX(ID) from TABLE_TEST where DISTRIBUTOR_ID="
										+ v.getDistributerId() + "");

						if (rs.next()) {
							maxId = rs.getInt(1);
						}
						System.out.println("ID======>" + maxId);
						psmt = con.prepareStatement(insertQuery);

						psmt.setInt(1, maxId + 1);
						psmt.setString(2, v.getLineCode());
						psmt.setString(3, v.getPartNumber());
						psmt.setString(4, v.getDescription());
						psmt.setDouble(5, v.getCostPrice());
						psmt.setDouble(6, v.getListPrice());
						psmt.setString(7, v.getUpc());
						psmt.setString(8, v.getQuantity());
						psmt.setInt(9, v.getLocation());
						psmt.setInt(10, v.getDistributerId());
						psmt.execute();

						System.out.println("Inserted Record====>"
								+ insertRecord++);
					}
				} finally {
					psmt.close();
					resultSet.close();

				}
				count++;
			}
			
			System.out.println("Total Record==" + count);
			System.out.println("Total Inserted Record=====>" + insertRecord);
			System.out.println("Updeted Records===========>" + updateRecord);
		} catch (SQLException sql) {

			sql.printStackTrace();
		} catch (Exception ee) {

			ee.printStackTrace();
		}

	}
}


 if(app.getId()!=0)
 sqlQuery +="ID="+app.getId();
 
 if(!"".equals(app.getAction()))
 sqlQuery +="and APPACTION='"+app.getAction().trim()+"'";




Rajnikant
(3:02:37 PM) File f = new File("path",true);
PrintWriter pout = new PrintWriter;
pout.println("yhehhefhef0";
(3:05:40 PM) import java.io.File;

public class FetchNames {

public static void main(String[] args) {

File folder = new File("D:\\Rajnikant Workspace\\25 nov 2015\\Original";
File[] listOfFiles = folder.listFiles();
for (File list : listOfFiles) {
//YourClassConstructor(list);
System.out.println(list.getName());
}

}

}








