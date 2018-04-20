

Use an ssh terminal such as PuTTY to connect to munro.humber.ca

Once logged in type

> [n12345678@munro ~]$ cd public_html

Create the directory:

> /home/students/n12345678/public_html/ceng254

Set appropriate permissions.

Change to that directory and create an index.jsp again with appropriate permissions.

Complete Learning Java Applications Chapter 6 in the lab using this environment by using the following instead:
```
<!-- will be hosted at http://munro.humber.ca/~n12345678/ceng254/index.jsp -->
<%@page import = "java.sql.*" %>
<%@page contentType="text/html" pageEncoding="UTF-8"%>
<!DOCTYPE html>
<html>
    <head>
        <meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
        <title>JSP Page</title>
    </head>
    <body>
        <h1>Hello World!</h1>
        <p>
        <ul>
         <%
                Connection c = DriverManager.getConnection("jdbc:oracle:thin:@apollo.humber.ca:1521:msit" ,"n12345678", "ORACLE");
                Statement s = c.createStatement();

                String query = ("SELECT * FROM medri.labtenstudent");
                ResultSet result = s.executeQuery(query);
                while (result.next()) {
                        %>
                        <li><%= result.getString("first_name") %></li>
                        <%
                }
                c.close();
          %>
        <ul>
        </p>
    </body>
</html>

'''

