# Using OData Services

  [Odata.org](http://odata.org/) provides a sample of the Northwind Database exposed as OData formatted services, this is a great resource for exploring the protocol.

The link below is to the Northwind service document, it lists all of the service operations, each operation represents a collection query-able data.

http://services.odata.org/Northwind/Northwind.svc/


To access the Customers collection we append the link provided above to the base url as follows

http://services.odata.org/Northwind/Northwind.svc/Customers/

We can accesses specific Customers via the links provided in the feed http://services.odata.org/Northwind/Northwind.svc/Customers(‘ALFKI’)

With the query string operations we can start to control the data provided, for example paging Customers 20 at a time.

http://services.odata.org/Northwind/Northwind.svc/Customers?$top=20 http://services.odata.org/Northwind/Northwind.svc/Customers?$skip=20&$top=20

Using filters we can search for Customers in a particular city or Products in our price range

http://services.odata.org/Northwind/Northwind.svc/Customers?$filter=City eq ‘London’

http://services.odata.org/Northwind/Northwind.svc/Products?$filter=UnitPrice le 200 and UnitPrice gt 100

Once we have found the data we wanted we can use the links to navigate to the related data. http://services.odata.org/Northwind/Northwind.svc/Suppliers(2)/Products

http://services.odata.org/Northwind/Northwind.svc/Products(5)/Order_Details

Finally we can format the response as JSON

http://services.odata.org/Northwind/Northwind.svc/Products(5)?$format=json



# Resources 

* [Whats new in OData 4.0](http://www.infoq.com/news/2013/05/OData-4)
