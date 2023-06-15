# Northwind-Grocery
Product Description:
The website being built is for "Northwind Grocery," a platform where users can search for food products sold by the grocery store. The website consists of two main pages: the home page and the product search page. The home page provides information about Northwind Grocery and includes a link to the product search page. On the product search page, users can search for products by category or view all products. The page displays a table of products with their ID, name, and price, and users can click on a product to view its details on the product details page.

Home Page:
The home page serves as an introduction to Northwind Grocery. It includes a navigation bar with a link to the home page itself (index.html) and a link to the product search page (products.html). The page can be customized with additional information about the grocery store, its values, or any other relevant content.

Product Search Page:
The product search page allows users to search for food products available at Northwind Grocery. It features a dropdown menu at the top where users can select the search criteria: "Select one..." (default option), "Search by category," or "View All." If users choose "View All," all products are immediately displayed in a table with relevant fields such as product ID, name, and price. Each product entry includes a "See Details" hyperlink that directs users to the product details page. If users choose "Search by category," another dropdown list appears, allowing users to select a specific category to filter the products.

Product Details Page:
The product details page (details.html) presents detailed information about a specific product. This page is accessed by clicking on the "See Details" link of a product on the product search page. It provides a space to display the product's details, such as its name, ID, price, category, and additional information. The page can be further customized to include any other relevant details about the product.

Interesting Code Snippet:
Here's an interesting code snippet from the script.js file that demonstrates how the product details are displayed dynamically on the product details page:

javascript
Copy code
// Get the product details from the query string and load the details page
function loadProductDetails() {
  const urlParams = new URLSearchParams(window.location.search);
  const productId = urlParams.get('id');

  if (!productId) {
    // Redirect to home page if product ID is not provided
    window.location.href = 'index.html';
  } else {
    fetch(`${apiUrl}/products/${productId}`)
      .then(response => response.json())
      .then(product => {
        // Display product details
        displayProductDetails(product);
      })
      .catch(error => console.error('Error:', error));
  }
}

// Display product details on the details page
function displayProductDetails(product) {
  const productDetailsContainer = document.getElementById('productDetails');

  productDetailsContainer.innerHTML = `
    <h2>${product.name}</h2>
    <p>ID: ${product.id}</p>
    <p>Price: ${product.price}</p>
    <p>Category: ${product.category}</p>
    <!-- Add additional product details here -->
  `;
}

// Load product details on page load
loadProductDetails();
In this code snippet, the loadProductDetails function retrieves the product ID from the query string in the URL of the product details page. It then makes a fetch request to the REST API endpoint to get the specific product details based on the ID. Once the response is received, the displayProductDetails function is called, which dynamically generates HTML markup to display the retrieved product's details on the product details page.

This code snippet showcases how data can be fetched from an API and dynamically displayed on a webpage, providing a seamless user experience when viewing product details.
