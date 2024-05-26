# e-commerce-app-js
A simple e-commerce app built with JavaScript, HTML, and CSS.

Objectives:
* HTML: content and structure; using semantically correct tags
* CSS: style and layout
* Client-side JavaScript: adding behavior and calling APIs
* Node.js: creating my own API
* SQL: providing data persistence in a relational database

| File          | Description |
|---------------|------------------------------|
|`public/index.html`|This file is the starting place for the entire front end of your website.|
|`public/styles.css`|This file contains the CSS styles for your front end.|
|`public/index.js`|This file contains the client-side JavaScript, which will call the API in `app.js` and provides other front end behavior for the features implemented.|
|`app.js`|This file contains the Node.js service that is the back end API.|
|`<insert-file-name>.db`|This file contains the database for the website.|
|`package.json`|This file contains the project dependencies (e.g. `express`) which are initialized using `npm init`.|
|`APIDOC.md`|This file is used to document the `app.js` web service.|
|`tables.sql`|This file includes any CREATE statements used in the database.|

## Features
### Feature 1: display the items on a “main view” page
Front End
  * A way for the user to be able to browse through all items
  * A way for the user to toggle between 2 layouts.

Back End
  * Endpoint to retrieve all items

### Feature 2: allow the user to login to their account
Front End
  * A way for the user to provide a valid username and password to gain access to account-required actions
  * A way for the user to allow the browser to save their username across browser sessions

Back End
  * Endpoint to check if the username and password match an entry in the database

### Feature 3: clicking on any individual item brings the user to a view which provides more detailed information about said item
Front End
  * This is implemented by using JS/DOM manipulation

Back End
  * Endpoint to retrieve detailed item information

### Feature 4: users are able to buy a product
Front End
  * Users must be logged in to make the purchase/enroll/reserve
  * The user can buy one productat a time
  * A way for the user to confirm and submit the transaction (these are two separate actions)
    * The user should not be able to change their transaction after confirming it.
  * After a successful transaction, the user is given a confirmation number

Back End
  * Endpoint to check if transaction is successful or not
  * If the transaction is successful, update the database, and return a generated confirmation code
  * Users are not able to buy products that are out of stock

### Feature 5: users are able to search and filter the available items
Front End
  * Implement a search bar
    * Are able to search multiple types of information
    * Are able to type in the search bar
  * Implement a way to filter items (e.g. displaying only pants, only classes that start with CSE, only reservations in the Bahamas, etc.)
    * Are able to toggle filters on and off

Back End
  * Endpoint to search database and return results

### Feature 6: users must be able to access all previous transactions
Front End
  * Users must be logged in
  * Users are able to view information about their transaction including but not limited to the name of the item and the confirmation number for each transaction

Back End
  * Endpoint to retrieve transaction history for any given user
  * The user must be **logged in**

### Feature 7: Feedback on a Product
  * Logged-in users are able to give feedback/rating/review on any given product
  * This uses a numerical rating scheme (e.g. 1-5, 1-10, etc.)
  * There is an “average rating” visibly shown for any given product.

### Feature 8: Recommendations
  * The website displays some “recommended” products for the user to look through.
  * The algorithm to choose “recommended” products is based on the purchase history of the user and other users that purchased similar things.

## Technologies
- JavaScript
- HTML
- CSS
