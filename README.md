# Servlet interview questions:
# 1) How many objects of a servlet is created?
 * Only one object at the time of first request by servlet or web container.

# 2) What is the life-cycle of a servlet?
* Servlet is loaded
* servlet is instantiated
* servlet is initialized
* service the request
* servlet is destroyed
# 3) What are the life-cycle methods for a servlet?
* public void init(ServletConfig config)	It is invoked only once when first request comes for the servlet. It is used to initialize the servlet.
* public void service(ServletRequest request,ServletResponse)throws ServletException,IOException	It is invoked at each request.The service() method is used to service the request.
* public void destroy()	It is invoked only once when servlet is unloaded.
# 4) Who is responsible to create the object of servlet?
* The web container or servlet container.

# 5) When servlet object is created?
* At the time of first request.

# 6) What is difference between Get and Post method?
* Get	Post
* 1) Limited amount of data can be sent because data is sent in header.post	Large amount of data can be sent because data is sent in body.
* 2) Not Secured because data is exposed in URL bar.post	Secured because data is not exposed in URL bar.
* 3) Can be bookmarked	.post Cannot be bookmarked
* 4) get is Idempotent.post is	Non-Idempotent
* 5) It is more efficient and used than Post	.post is less efficient and used
# 7) What is difference between PrintWriter and ServletOutputStream?
* PrintWriter is a character-stream class where as ServletOutputStream is a byte-stream class. The PrintWriter class can be used to write only character-based information whereas ServletOutputStream class can be 
* used to write primitive values as well as character-based information.
# 8) What is difference between GenericServlet and HttpServlet?
The GenericServlet is protocol independent whereas HttpServlet is HTTP protocol specific. HttpServlet provides additional functionalities such as state management etc.

# 9) What is servlet collaboration?
When one servlet communicates to another servlet, it is known as servlet collaboration. There are many ways of servlet collaboration:

RequestDispacher interface
sendRedirect() method etc.
# 10) What is the purpose of RequestDispatcher Interface?
The RequestDispacher interface provides the facility of dispatching the request to another resource it may be html, servlet or jsp. This interceptor can also be used to include the content of antoher resource.
# 11) Can you call a jsp from the servlet?
Yes, one of the way is RequestDispatcher interface for example:

RequestDispatcher rd=request.getRequestDispatcher("/login.jsp");  
rd.forward(request,response);  
# 12) Difference between forward() method and sendRedirect() method ?
forward() method	sendRedirect() method
1) forward() sends the same request to another resource.	1) sendRedirect() method sends new request always because it uses the URL bar of the browser.
2) forward() method works at server side.	2) sendRedirect() method works at client side.
3) forward() method works within the server only.	3) sendRedirect() method works within and outside the server.
# 13) What is difference between ServletConfig and ServletContext?
The container creates object of ServletConfig for each servlet whereas object of ServletContext is created for each web application.

# 14) What is Session Tracking?
Session simply means a particular interval of time.

Session Tracking is a way to maintain state of an user.Http protocol is a stateless protocol.Each time user requests to the server, server treats the request as the new request.So we need to maintain the state of an user to recognize to particular user.
# 15) What are Cookies?
A cookie is a small piece of information that is persisted between the multiple client requests. A cookie has a name, a single value, and optional attributes such as a comment, path and domain qualifiers, a maximum age, and a version number.
# 16) What is difference between Cookies and HttpSession?
Cookie works at client side whereas HttpSession works at server side.
# 17) What is filter?
A filter is an object that is invoked either at the preprocessing or postprocessing of a request. It is pluggable.
# 18) How can we perform any action at the time of deploying the project?
By the help of ServletContextListener interface.

# 19) What is the disadvantage of cookies?
It will not work if cookie is disabled from the browser.
# 20) How can we upload the file to the server using servlet?
One of the way is by MultipartRequest class provided by third party.
