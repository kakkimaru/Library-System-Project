# Executive summary of important application functionalities
Project is a web-based application that provides a range of functionalities for checking the availability of a reservation date, logging out a user, retrieving weather information, processing and modifying HTTP requests, and welcoming users. The application consists of several Java servlets and filters that work together to provide these functionalities. The doGet method of the AvailabilityCheckerServlet servlet is used to check the availability of a reservation date, the doGet method of the LogoutServlet servlet is used to revoke the user's SSO cookies and redirect them to the login page, the doGet method of the WeatherServlet servlet is used to retrieve weather information for a given city, the doFilter method of the SecondFilter filter is used to process and modify the request sent to it before it is sent to the target resource, the doGet method of the WelcomeServlet servlet is used to generate a response with a plain text message, the doFilter method of the FirstFilter filter is used to welcome a user by printing "Welcome" followed by the user's name in the response, and the doGet method of the UpperServlet servlet is used to convert a lowercase string input to an uppercase string output.

After analysis we have found following services: 
	1. class: com.acme.modres.AvailabilityCheckerServlet method: doGet
	2. class: com.acme.modres.LogoutServlet method: doGet
	3. class: com.acme.modres.WeatherServlet method: doGet
	4. class: com.acme.modres.SecondFilter method: doFilter
	5. class: com.acme.modres.WelcomeServlet method: doGet
	6. class: com.acme.modres.FirstFilter method: doFilter
	7. class: com.acme.modres.UpperServlet method: doGet.
We will summarize the functionality of each of them below.

## Summary of service with entry method: doGet in class: com.acme.modres.AvailabilityCheckerServlet
AvailabilityCheckerServlet is a Java servlet that checks the availability of a reservation date by comparing it with the dates of existing reservations. It receives the selected date as input and returns a JSON response with the availability status.
The doGet method of AvailabilityCheckerServlet handles the HTTP GET request to check the availability of the selected date. It parses the selected date from the request parameter and sets it as the selected date in the ReservationCheckerData MBean. It then retrieves the list of reservations from the ReservationCheckerData MBean and iterates through the list to check if there is a reservation that conflicts with the selected date.
If there is no conflict, the availability is set to true and the response status code is set to 200 (OK). If there is a conflict, the availability is set to false and the response status code is set to 201 (Created). In both cases, the response is a JSON object with the availability status.
The business purpose of AvailabilityCheckerServlet is to provide an API for checking the availability of a reservation date, which is useful for booking applications. The input to the servlet is the selected date and the output is a JSON response with the availability status.
The functional summary of the servlet includes the following methods:
doGet: This method handles the HTTP GET request to check the availability of the selected date.
setSelectedDate: This method sets the selected date in the ReservationCheckerData MBean.
getReservationList: This method retrieves the list of reservations from the ReservationCheckerData MBean.
isConflict: This method checks if there is a conflict with the selected date by iterating through the list of reservations.
setAvailability: This method sets the availability status in the ReservationCheckerData MBean.
sendResponse: This method sends the response with the availability status as a JSON object.
## Summary of service with entry method: doGet in class: com.acme.modres.LogoutServlet
The purpose of the LogoutServlet app is to revoke the user's SSO cookies and redirect them to the login page.
Input: The doGet method takes an HttpServletRequest and HttpServletResponse object as input.
Output: The doGet method returns a redirect to the login page.
Methodology:
The doGet method calls the WSSecurityHelper.revokeSSOCookies method to revoke the user's SSO cookies.
The WSSecurityHelper.revokeSSOCookies method uses the HttpServletRequest and HttpServletResponse objects to remove the JSESSIONID cookie and invalidate the session.
The doGet method then redirects the user to the login page.
## Summary of service with entry method: doGet in class: com.acme.modres.WeatherServlet
1. Business purpose:
The WeatherServlet app is a Java servlet that provides weather information to users. The app utilizes a third-party weather API to retrieve real-time weather information for a given city, and returns the information to the user in JSON format.
2. Input and Output:
Input:
The WeatherServlet app takes in a request from a user, which includes the name of the city for which weather information is requested.
Output:
The WeatherServlet app returns weather information for the requested city in JSON format.
3. Methodology:
The WeatherServlet app utilizes the doGet method to handle HTTP GET requests from users. When a GET request is received, the app retrieves the weather information for the requested city from a third-party weather API. The app then returns the weather information to the user in JSON format.
The getRealTimeWeatherData method is called by the doGet method to retrieve weather information from the third-party weather API. The method constructs a REST API request URL based on the requested city and the weather API key. The method then makes an HTTP GET request to the weather API and retrieves the weather information in JSON format.
The getDefaultWeatherData method is called by the doGet method if the weather API key is not found in the system environment variables. The method provides default weather information for a few cities, such as Paris, Las Vegas, San Francisco, Miami, Cork, and Barcelona.
The DefaultWeatherData class provides the default weather information for the selected city. The class loads the default weather data from a JSON file for the selected city, and returns the data to the WeatherServlet app.
## Summary of service with entry method: doFilter in class: com.acme.modres.SecondFilter
The purpose of the SecondFilter app is to process and modify the request sent to it before it is sent to the target resource. The filter reads the request content and appends the string " to our site!"to it, before sending the modified request on to the target resource.
The input to the SecondFilter app is the request sent by the client, and the output is the modified request with the added text.
The doFilter method utilizes the BufferedReader and PrintWriter classes to read and write the request content, and the FilterChain class to pass the modified request on to the target resource.
## Summary of service with entry method: doGet in class: com.acme.modres.WelcomeServlet
WelcomeServlet app is a simple Servlet program that generates a response with a plain text message "Enjoy!" for HTTP GET requests.
The purpose of this app is to demonstrate the use of the doGet method, which is called by the server when a GET request is received. The doGet method sets the content type of the response to "text/plain", creates a PrintWriter object to write to the response, and writes the message "Enjoy!"to the response.
The input provided to WelcomeServlet app is an HTTP request, and the output returned by the app is a plain text response. The functional summary highlights the use of the response object to set the content type and write the response message.
## Summary of service with entry method: doFilter in class: com.acme.modres.FirstFilter
The purpose of the `FirstFilter` app is to welcome a user by printing "Welcome" followed by the user's name in the response. The filter checks if a user name is provided as a request parameter and prints the default user name ("defaultUser") if no user name is provided.
The input to the `FirstFilter` app is the HTTP request and the output is the HTTP response. The filter reads the user name from the request parameter "user" and prints "Welcome " followed by the user name in the response.
The `doFilter` method of the `FirstFilter` app utilizes the `HttpServletRequest` and `HttpServletResponse` objects to read the user name from the request parameter and write the response. The filter also calls the `doFilter` method of the `FilterChain` object to pass the request and response on to the next filter in the chain.
## Summary of service with entry method: doGet in class: com.acme.modres.UpperServlet
UpperServlet app is a simple Java servlet that converts a lowercase string input to an uppercase string output. The purpose of this app is to illustrate the use of request parameters and response writing in a Java servlet.
The doGet method of UpperServlet takes in a request and response object as parameters and sets the content type of the response to text/html. It then retrieves the input string from the request parameter "input", converts it to uppercase, encodes the uppercase string, and writes it to the response output as HTML.
The business purpose of the output generated by UpperServlet is to convert a lowercase string input to an uppercase string output. The input string is retrieved from the request parameter "input", converted to uppercase, and returned in the response output.
The input to UpperServlet is a lowercase string provided in the request parameter "input". The output is an uppercase string written to the response output as HTML.
The functional summary of UpperServlet illustrates how the request parameter is retrieved, the string is converted to uppercase, and the uppercase string is written to the response output.
