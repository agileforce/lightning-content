# OData Overview 

  OData (Open Data Protocol) is an open standard (OASIS) to allow the simple creation & consumption of queryable and interoperable RESTful APIs.

> OData helps you focus on your business logic while building RESTful APIs without having to worry about the approaches to define request and response headers, status codes, HTTP methods, URL conventions, media types, payload formats and query options etc. 
  
> OData also guides you about tracking changes, defining functions/actions for reusable procedures and sending asynchronous/batch requests etc. Additionally, OData provides facility for extension to fulfil any custom needs of your RESTful APIs.


## Understanding OData in 6 steps

### Step 1: Requesting resources


> REST principle: “Everything is a Resource”. 

Lets start by requesting a resource from an OData source.

 resources can be retrieved from the OData RESTful APIs. The sample service used is the TripPin service which simulates the service of an open trip management system. Our friend, Russell White, who has formerly registered TripPin, would like to find out who are the other people in it.

HTTP request
C#  
Olingo JavaScript client
C++
Contribute
GET http://services.odata.org/v4/TripPinServiceRW/People HTTP/1.1
OData-Version: 4.0
OData-MaxVersion: 4.0
View the response

Step 2: Requesting an individual resource

REST principles also say, that every resource is identified by a unique identifier. OData also enables defining key properties of a resource and retrieving it using the keys. In this step, Russell wants to find the information about himself by specifying his username as the key.

HTTP request
C#  
Olingo JavaScript client
C++
Contribute
GET http://services.odata.org/v4/TripPinServiceRW/People('russellwhyte') HTTP/1.1
OData-Version: 4.0
OData-MaxVersion: 4.0
View the response

Step 3: Queries

As an architecture that’s built on top of the current features of the Web, RESTful APIs can also support query strings. For that, OData defines a series of system query options that can help you construct complicated queries for the resources you want. With the help of that, our friend Russell can find out the first 2 persons in the system who have registered at least one trip that costs more than 3000, and only display their first name and last name.

HTTP request
C#  
Olingo JavaScript client
C++
Contribute
GET http://services.odata.org/v4/TripPinServiceRW/People?$top=2 & $select=FirstName, LastName & $filter=Trips/any(d:d/Budget gt 3000) HTTP/1.1
OData-Version: 4.0
OData-MaxVersion: 4.0
View the response

Step 4: Creating a new resource

REST principles require the using of simple and uniform interfaces. With that regard, OData clients can expect unified interfaces of the resources. The stateless tranfer of representations in REST are carried out by using different HTTP methods in the requests. After having gone through the first 3 steps, Russell thinks the system is useful. He wants to add his best friend Lewis to the system. He finds out that all he needs to do is to send a POST request containing a JSON representation of Lewis’ information to the same interface from which he requested the people information.

HTTP request
C#  
Olingo JavaScript client
C++
Contribute
POST http://services.odata.org/v4/(S(34wtn2c0hkuk5ekg0pjr513b))/TripPinServiceRW/People HTTP/1.1
OData-Version: 4.0
OData-MaxVersion: 4.0
Content-Length: 428
Content-Type: application/json
 
{
    "UserName":"lewisblack",
    "FirstName":"Lewis",
    "LastName":"Black",
    "Emails":[
        "lewisblack@example.com"
    ],
    "AddressInfo":[
        {
            Address: "187 Suffolk Ln.",
            City: {
                CountryRegion: "United States",
                Name: "Boise",
                Region: "ID"
            }
        }
    ],
    "Gender": "Male",
    "Concurrency":635519729375200400
}
View the response

Step 5: Relating resources

In RESTful APIs, resources are usually dependent with each other. For that, the concept of relationships in OData can be defined among resources to add flexibility and richness to the data model. For example, in the TripPin OData service, people are related to the trips that they’ve booked using the system. Knowing that, Russell would like to invite Lewis to his existing trip in the U.S. by relating that trip to Lewis.

HTTP request
C#  
Olingo JavaScript client
C++
Contribute
POST http://services.odata.org/v4/(S(34wtn2c0hkuk5ekg0pjr513b))/TripPinServiceRW/People('lewisblack')/Trips/$ref HTTP/1.1
OData-Version: 4.0
OData-MaxVersion: 4.0
Content-Length: 123
Content-Type: application/json
 
{
    "@odata.id":"http://services.odata.org/V4/(S(34wtn2c0hkuk5ekg0pjr513b))/TripPinServiceRW/People('russellwhyte')/Trips(0)"
}
View the response

Step 6: Invoking a function

In RESTful APIs, there can be some custom operations that contain complicated logic and can be frequently used. For that purpose, OData supports defining functions and actions to represent such operations. They are also resources themselves and can be bound to existing resources. After having explored the TripPin OData service, Russell finds out that the it has a function called GetInvolvedPeople from which he can find out the involved people of a specific trip. He invokes the function to find out who else other than him and Lewis goes to that trip in the U.S.

HTTP request
C#  
Olingo JavaScript client
C++
Contribute
GET http://services.odata.org/v4/(S(34wtn2c0hkuk5ekg0pjr513b))/TripPinServiceRW/People('russellwhyte')/Trips(0)/Microsoft.OData.SampleService.Models.TripPin.GetInvolvedPeople()
HTTP/1.1
OData-Version: 4.0
OData-MaxVersion: 4.0
View the response




# Resources 

* [OData.org](http://www.odata.org/)  
