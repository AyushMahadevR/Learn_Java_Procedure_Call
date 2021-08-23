# How to call stored procedure from java.

- Represent parameters with ***standard parameter markers (?)*** or ***named parameter markers***.

- CallableStatement.execute(1 or many) ---> returns multiple result sets / unknown number of result sets.

- CallableStatement.executeQuery(1) ---> returns one result set.

- CallableStatement.executeUpdate(null) ---> return no result sets.



```java
int ifcaret;
int ifcareas;
int xsbytes;
String errbuff;
Connection con;
CallableStatement cstmt;
ResultSet rs;
…
cstmt = con.prepareCall("CALL DSN8.DSN8ED2(?,?,?,?,?)");                
                                  // Create a CallableStatement object
cstmt.setString (1, "DISPLAY THREAD(*)");                               
                                  // Set input parameter (Db2 command) 
cstmt.registerOutParameter (2, Types.INTEGER);                          
                                  // Register output parameters
cstmt.registerOutParameter (3, Types.INTEGER);
cstmt.registerOutParameter (4, Types.INTEGER);
cstmt.registerOutParameter (5, Types.VARCHAR);
cstmt.executeUpdate();            // Call the stored procedure         
ifcaret = cstmt.getInt(2);        // Get the output parameter values    
ifcareas = cstmt.getInt(3);
xsbytes = cstmt.getInt(4);
errbuff = cstmt.getString(5);
cstmt.close();                                                         
```
