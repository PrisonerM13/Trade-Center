# Trade Center
![Shopping](https://github.com/PrisonerM13/Trade-Center/blob/master/gif/Shopping.gif "Shopping")

### Features/Technologies/Tools:
+ Asp.Net Mvc 5
+ Asp.Net AJAX
+ jQuery AJAX
+ jQuery.UI
+ jQuery.Validation
+ Bootstrap
+ Responsive Design
+ Cross-Browser support
+ Modernizr
+ Entity Framework 6
+ SQL Server Local DB

### Operations Examples
+ #### Responsive Design
		
	![Responsive Design](https://github.com/PrisonerM13/Trade-Center/blob/master/gif/AdaptiveDisplay.gif "Responsive Design")

+ #### Register
		
	![Register](https://github.com/PrisonerM13/Trade-Center/blob/master/gif/Register.gif "Register")

+ #### Add Product
		
	![Add Product](https://github.com/PrisonerM13/Trade-Center/blob/master/gif/AddProduct.gif "Add Product")

+ #### Edit Product
		
	![Edit Product](https://github.com/PrisonerM13/Trade-Center/blob/master/gif/EditProduct.gif "Edit Product")

+ #### Sort
		
	![Sort](https://github.com/PrisonerM13/Trade-Center/blob/master/gif/Sort.gif "Sort")

### Rules
+ A user must be registerd in order to buy or sell. Viewing does not require registration.
+ Each product is advertised separatly, meaning quantity is always 1.
+ When a user enters a product's page, the product's state changes to "On Hold", meaning it's being saved for that user, until he leaves the page.
+ Only available-for-sale products are being displayed at home page.
+ A user can edit/delete products that he advertised, and buy products that others advertised.

### Product states
| State Name  | Description                               | State Code (in DB) |
| ----------- | ----------------------------------------- |:------------------:|
| Available   | Product is available for sale             |0                   |
| InCart      | Product has been added to a shopping cart |1                   |
| OnHold      | Product is currently being viewed         |2                   |
| Sold        | Product has been sold                     |3                   |

### Database
| Property       | Value                  |
| -------------- | ---------------------- |
| Engine         | Microsoft SQL Server   |
| Server Name    | (LocalDb)\MSSQLLocalDB |
| DB Name        | TradeCenter            |
| Authentication | Windows Authentication |

### Tables
![ERD](https://github.com/PrisonerM13/Trade-Center/blob/master/images/ERD.png "ERD")
		
* UserID & ProductID fields are auto generated by DB.
* Product's OwnerID is set to publishing user's Id and then to buying user's Id.
* Product's UserID is set to currently watching user's Id.
		
> The first time it's lanched, the application generates 10 random users and 12 constant products.
> User names and passwords are formatted as "userXX" and "passXX" respectevly, where XX is a 2 digit number between 01 and 10.
> Each product is assigned to a random user, but the application assures that "user01" owns at least 2 products (just for comfortability).

### Views
+ The site consists of a shared layout, which contains a header and a body.
+ The header contains the site's logo/title, main navigation bar (collapsable) and a login partial view.
	+ The login partial view's content depends on whether a use is logged-in:
		+ If a user is NOT logged in, the panel consists of a login form and a registration link.
		+ If a user is logged in, the panel consists of a log out link, edit account link and "Advertise" button (Add Product).
+ The body is a place holder for all other views.

### Routes
| Route                 | Description                                                         |
| --------------------- | ------------------------------------------------------------------- |
| /Home/Index **(default)** | Hosts a _Products_ partial view, rendered by Ajax, consisting of one _Product_ partial view for each available-for-sale product. The view also contains a sort order radio buttons. |
| /Home/About           | A general description of the site (currently gibrish)               |
| /Account/Edit         | Edit exisitng user account                                          |
| /Account/Register     | Sign up a new account                                               |
| /Product/Add          | Add/Advertise a new product                                         |
| /Product/Details      | View an exisitng product                                            |
| /Product/Edit         | Edit an exisitng product                                            |
| /Shopping Cart        | View/Edit shopping cart and commit a checkout (buy items)           |
