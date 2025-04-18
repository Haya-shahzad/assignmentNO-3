<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Baking World</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <script>
    // Function 1: Toggle recipe visibility
    function toggleRecipe(id) {
      const recipe = document.getElementById(id);
      recipe.classList.toggle('hidden');
    }

    // Function 2: Handle form submission
    function submitForm() {
      const comment = document.getElementById('comment').value;
      if (comment) {
        alert(`Thank you for sharing your thoughts: ${comment}`);
      } else {
        alert('Please enter a comment before submitting.');
      }
    }

    // Function 3: Update cart total
    function updateCart(price) {
      const total = document.getElementById('cart-total');
      const currentTotal = parseFloat(total.innerText) || 0;
      total.innerText = (currentTotal + price).toFixed(2);
    }

    // Function 4: Clear cart
    function clearCart() {
      const total = document.getElementById('cart-total');
      total.innerText = '0.00';
      alert('Your cart has been cleared!');
    }

    // Function 5: Search recipes
    function searchRecipes() {
      const query = document.getElementById('search').value.toLowerCase();
      const recipeCards = document.querySelectorAll('.recipe-card');
      recipeCards.forEach(card => {
        const title = card.querySelector('.recipe-title').innerText.toLowerCase();
        card.style.display = title.includes(query) ? 'block' : 'none';
      });
    }

    // Function 6: Change theme
    function changeTheme(theme) {
      const body = document.body;
      body.className = theme === 'dark' ? 'bg-gray-900 text-white' : 'bg-gray-50 text-gray-900';
    }

    // Function 7: Count recipes
    function countRecipes() {
      const recipeCards = document.querySelectorAll('.recipe-card');
      alert(`There are ${recipeCards.length} recipes available.`);
    }

    // Function 8: Validate contact form
    function validateForm() {
      const name = document.getElementById('name').value;
      const email = document.getElementById('email').value;
      if (!name || !email.includes('@')) {
        alert('Please provide a valid name and email.');
        return false;
      }
      alert('Thank you for contacting us!');
      return true;
    }

    // Function 9: Add new recipe
    function addRecipe() {
      const recipeList = document.getElementById('recipe-list');
      const newRecipe = document.createElement('div');
      newRecipe.className = 'recipe-card bg-white shadow-lg rounded-lg p-6';
      newRecipe.innerHTML = `
        <h3 class="recipe-title text-xl font-semibold mb-2">New Recipe</h3>
        <p class="text-gray-700">Description of the new recipe.</p>
        <button class="bg-pink-500 text-white px-4 py-2 mt-4 rounded hover:bg-pink-600">View Recipe</button>
      `;
      recipeList.appendChild(newRecipe);
      alert('New recipe added successfully!');
    }

    // Function 10: Scroll to top
    function scrollToTop() {
      window.scrollTo({ top: 0, behavior: 'smooth' });
    }
  </script>
</head>
<body class="bg-gray-50 font-sans">

  <!-- Header -->
  <header class="bg-gradient-to-r from-pink-500 to-yellow-500 text-white shadow-lg sticky top-0 z-50">
    <div class="max-w-7xl mx-auto p-6 flex justify-between items-center">
      <h1 class="text-4xl font-bold">Baking World</h1>
      <nav>
        <a href="#home" class="text-white px-4 py-2 rounded hover:bg-pink-600">Home</a>
        <a href="#recipes" class="text-white px-4 py-2 rounded hover:bg-pink-600">Recipes</a>
        <a href="#community" class="text-white px-4 py-2 rounded hover:bg-pink-600">Community</a>
        <a href="#shop" class="text-white px-4 py-2 rounded hover:bg-pink-600">Shop</a>
      </nav>
      <button onclick="scrollToTop()" class="bg-yellow-500 text-white px-4 py-2 rounded hover:bg-yellow-600">Top</button>
    </div>
  </header>

  <!-- Home Section -->
  <section id="home" class="py-16 text-center">
    <h2 class="text-3xl font-bold mb-4">Welcome to Baking World</h2>
    <p class="text-lg mb-6">Explore recipes, tips, and shop for baking essentials!</p>
    <input type="text" id="search" placeholder="Search recipes..." class="border p-2 rounded" onkeyup="searchRecipes()">
    <button onclick="changeTheme('dark')" class="bg-blue-500 text-white px-4 py-2 rounded hover:bg-blue-600">Dark Mode</button>
    <button onclick="changeTheme('light')" class="bg-yellow-500 text-white px-4 py-2 rounded hover:bg-yellow-600">Light Mode</button>
  </section>

  <!-- Recipes Section -->
  <section id="recipes" class="py-16">
    <h2 class="text-3xl font-bold text-center mb-8">Recipes</h2>
    <div id="recipe-list" class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-6">
      <!-- Recipe Cards -->
      <div class="recipe-card bg-white shadow-lg rounded-lg p-6">
        <h3 class="recipe-title text-xl font-semibold mb-2">Chocolate Cake</h3>
        <p class="text-gray-700">A rich and decadent treat.</p>
        <button onclick="toggleRecipe('recipe1')" class="bg-pink-500 text-white px-4 py-2 mt-4 rounded hover:bg-pink-600">View Recipe</button>
        <div id="recipe1" class="hidden mt-4">
          <h4 class="text-lg font-bold">Ingredients:</h4>
          <ul class="list-disc list-inside">
            <li>2 cups flour</li>
            <li>1 cup sugar</li>
            <li>1/2 cup cocoa powder</li>
          </ul>
        </div>
      </div>
    </div>
    <button onclick="addRecipe()" class="bg-green-500 text-white px-4 py-2 mt-4 rounded hover:bg-green-600">Add Recipe</button>
  </section>

  <!-- Community Section -->
  <section id="community" class="py-16 bg-gray-100">
    <h2 class="text-3xl font-bold text-center mb-8">Community</h2>
    <form onsubmit="event.preventDefault(); submitForm();" class="max-w-md mx-auto bg-white shadow-lg rounded-lg p-6">
      <textarea id="comment" placeholder="Share your thoughts..." class="w-full border p-2 rounded mb-4"></textarea>
      <button type="submit" class="bg-purple-600 text-white px-4 py-2 rounded hover:bg-purple-700">Submit</button>
    </form>
  </section>

  <!-- Shop Section -->
  <section id="shop" class="py-16">
    <h2 class="text-3xl font-bold text-center mb-8">Shop</h2>
    <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-6">
      <div class="bg-white shadow-lg rounded-lg p-6">
        <h3 class="text-xl font-semibold mb-2">Baking Kit</h3>
        <p class="text-gray-700">$29.99</p>
        <button onclick="updateCart(29.99)" class="bg-red-500 text-white px-4 py-2 rounded hover:bg-red-600">Add to Cart</button>
      </div>
    </div>
    <p class="mt-4">Cart Total: $<span id="cart-total">0.00</span></p>
    <button onclick="clearCart()" class="bg-red-600 text-white px-4 py-2 rounded hover:bg-red-700">Clear Cart</button>
  </section>

  <!-- Footer -->
  <footer class="bg-gradient-to-r from-pink-500 to-yellow-500 text-white text-center p-6">
    <p>&copy; 2025 Baking World | All Rights Reserved</p>
  </footer>

</body>
</html># assignmentNO-3
