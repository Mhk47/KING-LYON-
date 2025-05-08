<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1" />
<title>ShopZone - Your Online Store</title>
<style>
  /* Reset and base */
  * {
    box-sizing: border-box;
  }
  body {
    margin: 0;
    font-family: 'Amazon Ember', Arial, sans-serif;
    background-color: #ededed;
    color: #0f1111;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
  }
  /* Amazon Ember imitation font fallback */
  @font-face {
    font-family: 'Amazon Ember';
    src: local('Arial Black'), local('Arial Bold'), local('Arial');
    font-weight: bold;
  }

  /* Container */
  .container {
    max-width: 1200px;
    margin: 0 auto;
    padding: 0 10px;
  }

  /* Header */
  header {
    background-color: #131921;
    color: white;
    padding: 10px 10px 10px 20px;
    display: flex;
    align-items: center;
    flex-wrap: wrap;
    position: sticky;
    top: 0;
    z-index: 100;
  }
  .logo {
    font-weight: 900;
    font-size: 28px;
    color: #febd69;
    margin-right: 20px;
    cursor: pointer;
    user-select: none;
    white-space: nowrap;
  }
  .search-bar {
    flex: 1 1 auto;
    display: flex;
    max-width: 600px;
    margin-right: 20px;
  }
  .search-bar input[type="text"] {
    flex-grow: 1;
    padding: 8px 12px;
    border: none;
    border-radius: 4px 0 0 4px;
    font-size: 16px;
  }
  .search-bar button {
    background-color: #febd69;
    border: none;
    padding: 9px 16px;
    font-weight: bold;
    border-radius: 0 4px 4px 0;
    cursor: pointer;
    transition: background-color 0.3s ease;
  }
  .search-bar button:hover {
    background-color: #f3a847;
  }
  nav {
    display: flex;
    gap: 18px;
    flex-wrap: wrap;
    font-size: 14px;
  }
  nav a {
    color: white;
    text-decoration: none;
    padding: 5px 8px;
    border-radius: 4px;
    user-select: none;
  }
  nav a:hover {
    background-color: #232f3e;
  }

  /* Banner */
  .banner {
    width: 100%;
    margin: 15px 0;
    height: 250px;
    background: url('https://images.unsplash.com/photo-1542831371-d531d36971e6?auto=format&fit=crop&w=1200&q=80') center/cover no-repeat;
    border-radius: 6px;
    position: relative;
    color: white;
  }
  .banner-text {
    position: absolute;
    bottom: 30px;
    left: 30px;
    max-width: 300px;
    background-color: rgba(0,0,0,0.5);
    padding: 18px 22px;
    border-radius: 6px;
    font-size: 28px;
    font-weight: bold;
    text-shadow: 1px 1px 2px black;
  }

  /* Main layout */
  main {
    display: flex;
    gap: 15px;
  }
  aside {
    flex: 0 0 220px;
    background-color: white;
    border-radius: 6px;
    padding: 15px;
    height: fit-content;
    box-shadow: 0 1px 4px rgb(0 0 0 / 0.1);
  }
  aside h2 {
    font-size: 20px;
    margin-bottom: 12px;
    color: #111;
  }
  aside ul {
    padding-left: 0;
    list-style: none;
  }
  aside li {
    margin-bottom: 8px;
  }
  aside button.category-btn {
    all: unset;
    cursor: pointer;
    color: #0073bb;
    font-weight: 600;
    font-size: 14px;
    user-select: none;
    transition: color 0.3s ease;
  }
  aside button.category-btn:hover,
  aside button.category-btn.active {
    color: #febd69;
    font-weight: 700;
  }

  /* Products grid */
  section.products {
    flex: 1 1 auto;
    display: grid;
    grid-template-columns: repeat(auto-fill,minmax(190px,1fr));
    gap: 18px;
  }
  article.product-card {
    background-color: white;
    border-radius: 6px;
    padding: 10px 10px 15px;
    display: flex;
    flex-direction: column;
    box-shadow: 0 1px 4px rgb(0 0 0 / 0.1);
    transition: box-shadow 0.3s ease;
    cursor: pointer;
    user-select: none;
  }
  article.product-card:hover {
    box-shadow: 0 4px 12px rgba(0,0,0,0.15);
  }
  .product-image {
    width: 100%;
    aspect-ratio: 1/1;
    object-fit: contain;
    border-radius: 6px;
    margin-bottom: 10px;
  }
  .product-title {
    font-size: 14px;
    font-weight: 600;
    color: #111;
    margin-bottom: 6px;
    flex-grow: 1;
  }
  .product-price {
    font-size: 16px;
    font-weight: bold;
    color: #b12704;
    margin-bottom: 6px;
  }
  .product-rating {
    color: #ffa41c;
    font-size: 14px;
    margin-bottom: 8px;
  }
  .product-button {
    background-color: #febd69;
    border: none;
    padding: 8px;
    font-weight: 700;
    border-radius: 4px;
    cursor: pointer;
    transition: background-color 0.3s ease;
    text-align: center;
    user-select: none;
  }
  .product-button:hover {
    background-color: #f3a847;
  }

  /* Footer */
  footer {
    margin-top: 40px;
    padding: 20px 10px;
    text-align: center;
    font-size: 13px;
    color: #555;
    background-color: #232f3e;
    user-select: none;
  }

  /* Responsive */
  @media (max-width: 900px) {
    main {
      flex-direction: column;
    }
    aside {
      flex: 1 1 auto;
      margin-bottom: 20px;
    }
    .search-bar {
      max-width: 100%;
      margin-right: 10px;
      margin-top: 8px;
    }
    nav {
      width: 100%;
      margin-top: 8px;
      justify-content: flex-start;
      gap: 8px;
    }
  }

  /* Mobile optimization - fit in 350px width and 600px height */
  @media (max-width: 400px) {
    body, html {
      max-width: 350px;
      max-height: 600px;
      overflow-x: hidden;
      overflow-y: auto;
    }
    header {
      padding: 10px 8px;
      font-size: 14px;
    }
    .banner {
      height: 160px;
    }
    .banner-text {
      font-size: 20px;
      max-width: 220px;
      bottom: 15px;
      left: 15px;
      padding: 12px 16px;
    }
    aside {
      padding: 10px;
      flex: none;
      width: 100%;
    }
    section.products {
      grid-template-columns: repeat(auto-fill,minmax(140px,1fr));
      gap: 12px;
    }
    article.product-card {
      padding: 8px 8px 12px;
    }
    .product-button {
      font-size: 13px;
      padding: 6px 8px;
    }
  }
</style>
</head>
<body>
<header>
  <div class="logo" aria-label="ShopZone logo">ShopZone</div>
  <form class="search-bar" role="search" onsubmit="event.preventDefault();filterProducts();">
    <input type="text" id="searchInput" placeholder="Search products..." aria-label="Search products" autocomplete="off" />
    <button type="submit" aria-label="Search button">Search</button>
  </form>
  <nav aria-label="Main navigation">
    <a href="#" tabindex="0">Today's Deals</a>
    <a href="#" tabindex="0">Customer Service</a>
    <a href="#" tabindex="0">Gift Cards</a>
    <a href="#" tabindex="0">Registry</a>
    <a href="#" tabindex="0">Sell</a>
  </nav>
</header>

<div class="container">
  <div class="banner" role="img" aria-label="Hero banner with shopping items">
    <div class="banner-text">Find the Best Deals Here!</div>
  </div>

  <main>
    <aside aria-label="Product Categories">
      <h2>Categories</h2>
      <ul>
        <li><button class="category-btn active" data-category="all" aria-pressed="true">All</button></li>
        <li><button class="category-btn" data-category="electronics" aria-pressed="false">Electronics</button></li>
        <li><button class="category-btn" data-category="clothing" aria-pressed="false">Clothing</button></li>
        <li><button class="category-btn" data-category="home" aria-pressed="false">Home & Kitchen</button></li>
        <li><button class="category-btn" data-category="books" aria-pressed="false">Books</button></li>
        <li><button class="category-btn" data-category="toys" aria-pressed="false">Toys & Games</button></li>
      </ul>
    </aside>
    <section class="products" aria-live="polite" aria-label="Product listings" id="productsGrid">

      <!-- Product Cards -->
      <article class="product-card" data-category="electronics" tabindex="0">
        <img src="https://images-na.ssl-images-amazon.com/images/I/61j0lUvc1-L._AC_SY450_.jpg" alt="Wireless Noise-Canceling Headphones" class="product-image" />
        <div class="product-title">Wireless Noise-Canceling Headphones</div>
        <div class="product-price">$89.99</div>
        <div class="product-rating" aria-label="4.5 stars out of 5">&#11088;&#11088;&#11088;&#11088;&#11088;&#9734;</div>
        <button class="product-button" aria-label="Add Wireless Noise-Canceling Headphones to cart">Add to Cart</button>
      </article>
      <article class="product-card" data-category="clothing" tabindex="0">
        <img src="https://images-na.ssl-images-amazon.com/images/I/81+n5lcMFDL._AC_UX569_.jpg" alt="Men's Classic Denim Jacket" class="product-image" />
        <div class="product-title">Men's Classic Denim Jacket</div>
        <div class="product-price">$59.99</div>
        <div class="product-rating" aria-label="4 stars out of 5">&#11088;&#11088;&#11088;&#11088;&#9734;&#9734;</div>
        <button class="product-button" aria-label="Add Men's Classic Denim Jacket to cart">Add to Cart</button>
      </article>
      <article class="product-card" data-category="home" tabindex="0">
        <img src="https://images-na.ssl-images-amazon.com/images/I/71UX85dpxaL._AC_SL1500_.jpg" alt="Stainless Steel Cookware Set" class="product-image" />
        <div class="product-title">12-Piece Stainless Steel Cookware Set</div>
        <div class="product-price">$129.99</div>
        <div class="product-rating" aria-label="4.7 stars out of 5">&#11088;&#11088;&#11088;&#11088;&#11088;&#9733;</div>
        <button class="product-button" aria-label="Add 12-Piece Stainless Steel Cookware Set to cart">Add to Cart</button>
      </article>
      <article class="product-card" data-category="books" tabindex="0">
        <img src="https://images-na.ssl-images-amazon.com/images/I/81eB+7+CkUL.jpg" alt="The Silent Patient" class="product-image" />
        <div class="product-title">The Silent Patient by Alex Michaelides</div>
        <div class="product-price">$14.49</div>
        <div class="product-rating" aria-label="4.3 stars out of 5">&#11088;&#11088;&#11088;&#11088;&#9734;&#9734;</div>
        <button class="product-button" aria-label="Add The Silent Patient by Alex Michaelides to cart">Add to Cart</button>
      </article>
      <article class="product-card" data-category="toys" tabindex="0">
        <img src="https://images-na.ssl-images-amazon.com/images/I/71c0ket8uXL._AC_SY679_.jpg" alt="Building Block Toy Set" class="product-image" />
        <div class="product-title">Building Block Toy Set for Kids</div>
        <div class="product-price">$24.99</div>
        <div class="product-rating" aria-label="4.6 stars out of 5">&#11088;&#11088;&#11088;&#11088;&#11088;&#9734;</div>
        <button class="product-button" aria-label="Add Building Block Toy Set for Kids to cart">Add to Cart</button>
      </article>
      <article class="product-card" data-category="electronics" tabindex="0">
        <img src="https://images-na.ssl-images-amazon.com/images/I/71rZGQUQRTL._AC_SY355_.jpg" alt="Smart Watch Fitness Tracker" class="product-image" />
        <div class="product-title">Smart Watch Fitness Tracker</div>
        <div class="product-price">$69.99</div>
        <div class="product-rating" aria-label="4 stars out of 5">&#11088;&#11088;&#11088;&#11088;&#9734;&#9734;</div>
        <button class="product-button" aria-label="Add Smart Watch Fitness Tracker to cart">Add to Cart</button>
      </article>
      <article class="product-card" data-category="clothing" tabindex="0">
        <img src="https://images-na.ssl-images-amazon.com/images/I/71xNgvVPhOS._AC_UX522_.jpg" alt="Women's Casual Sneakers" class="product-image" />
        <div class="product-title">Women's Casual Sneakers</div>
        <div class="product-price">$39.99</div>
        <div class="product-rating" aria-label="4.4 stars out of 5">&#11088;&#11088;&#11088;&#11088;&#9734;&#9734;</div>
        <button class="product-button" aria-label="Add Women's Casual Sneakers to cart">Add to Cart</button>
      </article>
      <article class="product-card" data-category="home" tabindex="0">
        <img src="https://images-na.ssl-images-amazon.com/images/I/71t5YOiAP3L._AC_SL1500_.jpg" alt="Soft Throw Blanket" class="product-image" />
        <div class="product-title">Soft and Cozy Throw Blanket</div>
        <div class="product-price">$22.49</div>
        <div class="product-rating" aria-label="4.1 stars out of 5">&#11088;&#11088;&#11088;&#9734;&#9734;&#9734;</div>
        <button class="product-button" aria-label="Add Soft and Cozy Throw Blanket to cart">Add to Cart</button>
      </article>
      <article class="product-card" data-category="books" tabindex="0">
        <img src="https://images-na.ssl-images-amazon.com/images/I/91uwocAMtSL.jpg" alt="Atomic Habits Book" class="product-image" />
        <div class="product-title">Atomic Habits by James Clear</div>
        <div class="product-price">$11.98</div>
        <div class="product-rating" aria-label="4.8 stars out of 5">&#11088;&#11088;&#11088;&#11088;&#11088;&#9733;</div>
        <button class="product-button" aria-label="Add Atomic Habits by James Clear to cart">Add to Cart</button>
      </article>

    </section>
  </main>
</div>

<footer>
  &copy; 2024 ShopZone. All rights reserved. Made with ❤️ for your shopping needs.
</footer>

<script>
  // Filtering products by category and search
  const categoryButtons = document.querySelectorAll('.category-btn');
  const products = document.querySelectorAll('.product-card');
  const searchInput = document.getElementById('searchInput');

  function setActiveCategory(button) {
    categoryButtons.forEach(btn => {
      btn.classList.remove('active');
      btn.setAttribute('aria-pressed', 'false');
    });
    button.classList.add('active');
    button.setAttribute('aria-pressed', 'true');
  }

  function filterProducts() {
    const searchTerm = searchInput.value.trim().toLowerCase();
    const activeCategoryBtn = document.querySelector('.category-btn.active');
    const category = activeCategoryBtn ? activeCategoryBtn.dataset.category : 'all';

    products.forEach(product => {
      const title = product.querySelector('.product-title').textContent.toLowerCase();
      const categoryMatch = category === 'all' || product.dataset.category === category;
      const searchMatch = title.includes(searchTerm);
      if(categoryMatch && searchMatch) {
        product.style.display = 'flex';
      } else {
        product.style.display = 'none';
      }
    });
  }

  categoryButtons.forEach(button => {
    button.addEventListener('click', () => {
      setActiveCategory(button);
      filterProducts();
    });
  });

  // Also filter on typing in the search input with debounce
  let debounceTimer;
  searchInput.addEventListener('input', () => {
    clearTimeout(debounceTimer);
    debounceTimer = setTimeout(filterProducts, 200);
  });

  // Initial filter to show all
  filterProducts();
</script>
</body>
</html>

```
