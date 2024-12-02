# Restful Booker API Performance Testing
This project evaluates the performance and reliability of the Restful Booker API under various conditions. Using Apache JMeter, this test plan is configured to simulate HTTP requests such as GET, POST, PUT, PATCH, and DELETE, targeting key API endpoints.

_**This test suite is designed to:**_
- Assess the system's responsiveness by measuring metrics like response time and throughput.
- Identify performance bottlenecks under increasing levels of concurrent user traffic.
- Ensure the API can handle typical operations like creating, updating, retrieving, and deleting bookings efficiently.

**Prerequisites**
1. _**System Requirements:**_
   - Operating System: Windows, Linux, or macOS
   - Java 8 or higher installed (required for JMeter)
2. _**Tools**_
   - Apache JMeter:  If you haven't already, [download and install Apache JMeter](https://jmeter.apache.org/download_jmeter.cgi).
3. _**Setup and Execution**_
   - Step 1: Clone the Repository:
     ``` clone
     git clone https://github.com/mdnazrulislam7255/Booikng_API_Load_Testing.git
     ```
   - Step 2: Configure JMeter
     Open the Restful_Booker.jmx file in Apache JMeter.
     Update the HTTP Request Defaults element to set the API base URL and authentication details (if applicable).
3. **_Import collection:_**
   - Open Jmeter.
   - Click on the Import button.
   - Select the file from the repository.

**Usage**
_**Select Environment:**_
      In Apache JMeter, select the appropriate environment from the top-right dropdown.
_**Run Collection:**_
      Select the imported collection.
      Select any one of the listener .
      Select the desired environment.
      Click Start Test to run the project.
_**View Results:**_
     Once the tests are complete, view the results in the listener like View Results Tree or Aggregate Report.
     Detailed test results can be viewed for each request.

# Base URL
The base URL is: https://restful-booker.herokuapp.com

# End points
_### **Health Check**_
Protocol : https                                                                                                                                                                          
Server Name or IP: restful-booker.herokuapp.com                                                                                                                                           
HTTP Request method: GET                                                                                                                                                                  
Path: /ping                                                                                                                                                                               
Request body: ```none```                                                                                                                                                                  
Response body: ```Created```                                                                                                                                                             

_### **Create Booking Token**_
Protocol : https                                                                                                                                                                          
Server Name or IP: restful-booker.herokuapp.com                                                                                                                                           
HTTP Request method: POST                                                                                                                                                                 
Path: /auth                                                                                                                                                                               
Request body:                                                                                                                                                                             
``` console
{
    "username" : "admin",
    "password" : "password123"
}
```
Response body:
``` console
{"token":"1ce98290ae3d1f2"}
```

_### **Create Booking **_
Protocol : https                                                                                                                                                                          
Server Name or IP: restful-booker.herokuapp.com                                                                                                                                           
HTTP Request method: POST                                                                                                                                                                 
Path: /booking                                                                                                                                                                            
Request body:                                                                                                                                                                             
``` console
{
    "firstname" : "Jim",
    "lastname" : "Brown",
    "totalprice" : 111,
    "depositpaid" : true,
    "bookingdates" : {
        "checkin" : "2018-01-01",
        "checkout" : "2019-01-01"
    },
    "additionalneeds" : "Breakfast"
}
```
Response body:
``` console
{"bookingid":4477,"booking":{"firstname":"Jim","lastname":"Brown","totalprice":111,"depositpaid":true,"bookingdates":{"checkin":"2018-01-01","checkout":"2019-01-01"},"additionalneeds":"Breakfast"}}
```

_### **Get Booking **_
Protocol : https                                                                                                                                                                          
Server Name or IP: restful-booker.herokuapp.com                                                                                                                                           
HTTP Request method: GET                                                                                                                                                                  
Path: booking/${booking_ID}                                                                                                                                                               
Request body: ``` none ```                                                                                                                                                                
Response body:                                                                                                                                                                            
``` console
{"firstname":"Jim","lastname":"Brown","totalprice":111,"depositpaid":true,"bookingdates":{"checkin":"2018-01-01","checkout":"2019-01-01"},"additionalneeds":"Breakfast"}
```

_### **Update Booking **_
Protocol : https                                                                                                                                                                          
Server Name or IP: restful-booker.herokuapp.com                                                                                                                                           
HTTP Request method: PUT                                                                                                                                                                  
Path: booking/${booking_ID}                                                                                                                                                               
Request body:                                                                                                                                                                             
``` console
{
    "firstname" : "Nazrul",
    "lastname" : "Islam",
    "totalprice" : 111,
    "depositpaid" : true,
    "bookingdates" : {
        "checkin" : "2018-01-01",
        "checkout" : "2019-01-01"
    },
    "additionalneeds" : "Breakfast"
}
```
Response body:
``` console
{"firstname":"Nazrul","lastname":"Islam","totalprice":111,"depositpaid":true,"bookingdates":{"checkin":"2018-01-01","checkout":"2019-01-01"},"additionalneeds":"Breakfast"}
```
_### **Update Booking Partially**_
Protocol : https                                                                                                                                                                          
Server Name or IP: restful-booker.herokuapp.com                                                                                                                                           
HTTP Request method: PATCH                                                                                                                                                                
Path: booking/${booking_ID}                                                                                                                                                               
Request body:                                                                                                                                                                             
``` console
{
  "firstname" : "Nafsi",
  "totalprice" : 500
}
```
Response body:
``` console
{"firstname":"Nafsi","lastname":"Islam","totalprice":500,"depositpaid":true,"bookingdates":{"checkin":"2018-01-01","checkout":"2019-01-01"},"additionalneeds":"Breakfast"}
```

_### **Delete Booking **_
Protocol : https                                                                                                                                                                          
Server Name or IP: restful-booker.herokuapp.com                                                                                                                                           
HTTP Request method: DELETE                                                                                                                                                               
Path: booking/${booking_ID}                                                                                                                                                               
Request body: ``` none```                                                                                                                                                                 
Response body: ``` Created```                                                                                                                                                             

### Run Command:
  Run Command for Report:
``` console
 jmeter -n -t Restful_Booker.jmx -l reports\Restful_Booker.jtl
```
``` console
 jmeter -g reports\Restful_Booker.jtl -o reports\Restful_Booker.html
```
### Reports
![image](https://github.com/user-attachments/assets/658a248c-d908-4598-8a55-70f66e0be330)



