```java
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;

public class JDBC {
	static final String JDBC_DRIVER = "com.mysql.jdbc.Driver";
	static final String DB_URL = "jdbc:mysql://localhost:3306/imooc";
	static final String USER = "root";
	static final String PASSWORD = "wang";
	public static void helloword() throws ClassNotFoundException {
		Connection conn = null;
		Statement stmt = null;
		ResultSet rs = null;
		//1.加载驱动程序
		Class.forName(JDBC_DRIVER);
		//2.建立数据库连接
		try {
			conn = DriverManager.getConnection(DB_URL,USER,PASSWORD);
			//3执行SQL语句
			stmt = conn.createStatement();
			rs = stmt.executeQuery("select user_name from imooc_goddess");
			//4.获取执行结果
			while(rs.next()){
				System.out.println("hello"+rs.getString("user_name"));
			}
		} catch (SQLException e) {
			// 异常处理
			e.printStackTrace();
		}finally{
			//5.清理环境
				try {
					if(conn!=null)
					conn.close();
					if(stmt!=null)
						stmt.close();
					if(rs!=null)
						rs.close();
				} catch (SQLException e) {
					// ignore
				}
			
			
		}
		
	}

	public static void main(String[] args) throws ClassNotFoundException {	
		helloword();
	}
}
```
NAVICAT配置如下：

（1）连接:任意名；

（2）新接数据库本例命名为imooc；

（3）建立表imooc_goddess;
