## Proxy Objects

**Easy Explanation:**  
Proxy objects in SAP ABAP are special programs or classes that act as a bridge between SAP and external systems (like web services). They help SAP communicate with other software by converting messages into a format both sides understand.

**Technical Explanation:**  
In ABAP, proxy objects are generated from WSDL (for web services) or XML schema definitions. There are two types:
- **Client Proxy:** Allows ABAP programs to call external web services as if they were local methods.
- **Server Proxy:** Exposes ABAP functionality as a web service to be called by external systems.

Proxy generation is done using transaction codes like `SPROXY`. The generated ABAP classes handle serialization, deserialization, and communication protocols (SOAP, HTTP, etc.), making integration seamless.


Prequiesite for proxy objects
    matchin structute type
        same number of compmenenes
        same componenets name
        same types


## OData Services from CDS Views

    **Easy Explanation:**  
    OData(Open Data) services from CDS views allow you to easily share SAP data with other applications over the web. Byexposing a CDS (Core Data Services) view as an OData service, you make SAP data available in a standardformat that can be read by web and mobile apps.

    **Technical Explanation:**  
    In ABAP, CDS views define data models at the database level. You can expose these views as OData servicesusing annotations like `@OData.publish: true` in the CDS view definition. This automatically generates anOData service, which can be activated and managed in the SAP Gateway (using transaction `/IWFNDMAINT_SERVICE`). The OData protocol enables CRUD operations (Create, Read, Update, Delete) on the data,supporting integration with external systems and UI frameworks like SAP Fiori.


SAP GaTEWAY INTRODUCTION