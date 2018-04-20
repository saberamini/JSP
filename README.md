  

Use an ssh terminal such as PuTTY to connect to munro.humber.ca

Once logged in type

> [n12345678@munro ~]$ cd public_html

Create the directory:

> /home/students/n12345678/public_html/ceng254

Set appropriate permissions.  Note that you need at least executable writes on all your directories.  To do this use the command:

> chmod o+x directoryName

Change to that directory and create an index.jsp again with appropriate permissions.

We now want to create a dynamic website that displays the a query as part of the HTML. Complete the page below to have this done.  If you haven't already done so, you can take a look at the <a href="https://www.lynda.com/Java-tutorials/Up-Running-Java-Applications/435790-2.html"> This video</a> to get some theory behind these commands.

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
                
                String query = ("SELECT * FROM STUDENT");
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

