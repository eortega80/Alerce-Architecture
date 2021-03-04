The Application architecture consists of three layers: client components, server components and data components.
On the client´s side, access to the main application services can be done through a browser, or by calling on specific APIs. On the server´s side, the application exits under two versions, depending on the module:

- Modern J2EE 7 application with JSF pages and beans fed from EJBs with JPA persistence.
- Older Struts based application (Pickups and Deliveries Modules) with JSP pages fed from Java Beans (filled with information from DAOs).

However, both application versions run on JBoss Application Server.
On the data´s side, and as mentioned above, there is an Oracle Database where common functionalities are run under the same package.

![Application Architecture Diagram](images/Architecture%20diagram.png)
