<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>My Link Collection - Designed by Suraj Kumar Nayak</title>
  <style>
    /* General Styles */
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }
    body {
      font-family: 'Arial', sans-serif;
      background: linear-gradient(135deg, #00c6ff, #0072ff);
      color: #2d3436;
      display: flex;
      justify-content: center;
      align-items: center;
      min-height: 100vh;
      padding: 20px;
    }
    .container {
      max-width: 900px;
      width: 100%;
      padding: 30px;
      background: #ffffff;
      box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
      border-radius: 8px;
    }
    h1 {
      text-align: center;
      margin-bottom: 20px;
      color: #0072ff;
      font-size: 2em;
    }
    .search-bar {
      margin-bottom: 20px;
      display: flex;
      justify-content: space-between;
    }
    .search-bar input {
      flex: 1;
      padding: 12px;
      border: 1px solid #ccc;
      border-radius: 5px;
    }
    .search-bar button {
      padding: 12px;
      background-color: #0072ff;
      color: white;
      border: none;
      border-radius: 5px;
      cursor: pointer;
      margin-left: 10px;
    }
    .search-bar button:hover {
      background-color: #0056b3;
    }
    ul {
      list-style: none;
      padding: 0;
    }
    li {
      background: #f7f7f7;
      margin: 10px 0;
      padding: 15px;
      border-radius: 8px;
      display: flex;
      justify-content: space-between;
      align-items: center;
      box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
      transition: all 0.3s ease;
    }
    li:hover {
      background: #ebf5ff;
    }
    a {
      text-decoration: none;
      color: #0072ff;
      font-weight: bold;
    }
    a:hover {
      text-decoration: underline;
    }
    button.delete-btn {
      background: #d63031;
      border: none;
      color: #fff;
      padding: 5px 10px;
      border-radius: 5px;
      cursor: pointer;
    }
    button.delete-btn:hover {
      background: #e17055;
    }
    .add-link {
      display: flex;
      margin-top: 30px;
    }
    .add-link input {
      flex: 1;
      padding: 12px;
      border: 1px solid #ccc;
      border-radius: 5px;
    }
    .add-link button {
      padding: 12px;
      background: #0072ff;
      color: white;
      border: none;
      border-radius: 5px;
      cursor: pointer;
      margin-left: 10px;
    }
    .add-link button:hover {
      background: #0056b3;
    }
    .footer {
      text-align: center;
      margin-top: 20px;
      font-size: 0.9em;
      color: #636e72;
    }
    /* Responsive Design */
    @media (max-width: 768px) {
      .container {
        padding: 20px;
      }
      h1 {
        font-size: 1.5em;
      }
    }
  </style>
</head>
<body>
  <div class="container">
    <h1>My Link Collection - Designed by Trending Fashion Deals & Team</h1>

    <!-- Search Bar -->
    <div class="search-bar">
      <input type="text" id="search-input" placeholder="Search your links...">
      <button onclick="searchLinks()">Search</button>
    </div>

    <!-- Link List -->
    <ul id="link-list">
      <!-- Links will appear here -->
    </ul>

    <!-- Add New Link -->
    <div class="add-link">
      <input type="text" id="new-link" placeholder="Paste your link here">
      <button onclick="addLink()">Add Link</button>
    </div>
    <div class="footer">Designed with ❤️Treandind fashion deals & Team</div>
  </div>

  <script>
    const linkList = document.getElementById('link-list');
    const searchInput = document.getElementById('search-input');
    let links = [];

    // Add new link function
    function addLink() {
      const linkInput = document.getElementById('new-link');
      const linkValue = linkInput.value.trim();

      if (linkValue) {
        const linkObj = { url: linkValue, id: Date.now() };
        links.push(linkObj);
        renderLinks();
        linkInput.value = '';
      } else {
        alert('Please enter a valid link!');
      }
    }

    // Render all links
    function renderLinks(filter = '') {
      linkList.innerHTML = '';
      const filteredLinks = links.filter(link =>
        link.url.toLowerCase().includes(filter.toLowerCase())
      );

      filteredLinks.forEach(link => {
        const li = document.createElement('li');
        li.innerHTML = `
          <a href="${link.url}" target="_blank">${link.url}</a>
          <button class="delete-btn" onclick="deleteLink(${link.id})">Delete</button>
        `;
        linkList.appendChild(li);
      });
    }

    // Delete link function
    function deleteLink(id) {
      links = links.filter(link => link.id !== id);
      renderLinks();
    }

    // Search links
    function searchLinks() {
      const filter = searchInput.value.trim();
      renderLinks(filter);
    }
  </script>
</body>
</html>
