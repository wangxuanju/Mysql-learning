# 场景三：大字段
读取数据库表大字段；即使读取一条记录，也有可能记录太大了，出现内存溢出的问题；采取流方式，大字段以二进制的方式进行划分，分为多个区间，每次读取一个区间；
流方式使用ResultSet.getBinaryStream()方法；
读取数据库大字段：使用流方式
```java
//函数（方法）中的内容
	Connection conn = null;
	PreparedStatement ptmt = null;
	ResultSet rs = null;
	try{
		//1.加载数据库驱动
		Class.forName(JDBC_DRIVER);
		//2.建立数据库连接
		conn = DriverManager.getConnection(DB_URL,USER,PASSWORD);
		//3创建PreparedStatement对象
		String sql = "select * from user_note";
		ptmt = conn.prepareStatement(sql);
		//4执行SQL语句
		rs = ptmt.executeQuery();
		while(rs.next()){
			//5获取对象流
			InputStream in = rs.getBinaryStream("blog");//主要是这个方法
			File f = new File(FILE_URL);
			OutputStream out = null;
			out = new FileOutputStream(f);
			int temp = 0;
			while((temp = in.read()) != -1){//边读边写
				out.write(temp);
			}
			in.close();
			out.close();
		}	
	}catch(SQLException e){
  // ignore
  }
``` 
