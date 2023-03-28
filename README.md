    assignment-3-team3


Chocoland Website with Servlet as a Maven project using Tomcat 9.x Server.

    The website consists of four main pages:

   * Home
   * Product
   * My orders
   * Cart
   
    Below are the responsibilities of each servelet:
    
   * CartServlet: creates a cart object as a session attribute, includes the product into the cart by retrieving it from the database. 
     Checks if the product already exists in the cart. After the product was placed in the cart attribute, forwards to the the cartContents.jsp.
   * HeaderServlet: generates the navbar and is included by other servlets in order to display it in all other pages that need a navbar.
   * OrderSubmitServlet: sends the validated data from the order form to the database.
   * PreviousOrdersServlet: retrieves the last 5 orders from the database, as well as has their ratings. The ratings are adjusted (the right amount
     of stars are highlighted) depending on the rating value.
   * ProductDetailsServlet: retrives the product details from the database and displays the results. Allows the user to add a product into the cart
   * ProductsServlet: generates all the possible products that exist in the database and places them in different sections depending on the category. 
     The ProductDetailsServlet is potentially called when a product is selected.
   * RatingServlet: When a rating is submitted for one of the last 5 orders in the PreviousOrdersServlet, sends that rating to the database, 
     and then redirects to the PreviousOrders page.
     
     
     
    Below are other classes that were created to follow the single-responsibility principle:
    
   * CartItem - for storing each cart item, which might include a multiple number of a product in it. Cart Item = Multiple Number of the same Product.
   * generateProducts - generates Product objects by parsing the chocolates.csv file
   * JDBCCredentials - declares all the credentials required to connect to the localhost mySQL database on port 3306.
   * MySQLJDBC.java - handles the creation of all required tables and also requests sent from the servlets to insert values into a particular table.
   * Order.java - stores the Order as an object for eaiser retrieval of the values while in tranfer from servlet to database.
   * Product.java - for storing a product and its attributes.
   
    Below are .jsp and .html files:
   
   * cartContent.jsp - shows the cart contents and the form
   * confirmation.jsp - shows the confirmation page with the order details
   * index.html       - serves as a home page. 
  
   
   
    Database Tables
   
   * Orders        - stores all the information about places orders
   * OrderDetails  - stores the details about each order, where number of the OrderID correspond to the order in the Orders table
   * Products      - stores all the information about the products
   
    
    How and where are the requirements satisfied 
    
   * First requirement:
     First servlet  = ProductsServlet dynamically generates the list of products.
     Second servlet = PreviousOrdersServlet generates the last 5 orders
     Rating requirement is handled by the RatingServlet along with PreviousOrdersServlet.
     request.incude() feature was used in almost every servlet which required a navbar.
   * Second requirement:
     ProductDetailsServlet generates the detail page according to the product ID and has a Add To Cart button which sends a response to CartServlet.
   * Third requirement:
     A form submission and database insertion is handled by OrderSubmitServlet, the data is validated before sending the request in the 
     cartContents.jsp
   * Fourth requirement:
     CartServlet creates a check-out page with all of the products, their quantity, and other key information, as well as shows the total.
     This servlet allows the user to fill-out the form. The orderSubmit servlet helps with sending the form to the database and
     takes care of forwarding the request to the confirmation page after a successful submission.
     Uses request.getRequestDispatcher().forward() method to forward to the cartContents.jsp file. 
   * Fifth requirement: unfortunately, not implemented (extra credit)
    
