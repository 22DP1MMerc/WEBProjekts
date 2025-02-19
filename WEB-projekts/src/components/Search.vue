<template>
    <div class="search-container">
        <input type="text" id="search" placeholder="Search...">
        <button onclick="searchFunction()">Search</button>
    </div>
  </template>
  
  <script>
  function searchFunction() {
      const query = document.getElementById('search').value;
      alert("Searching for: " + query);
  }
</script>

<style scoped>
.search-container {
    display: flex;
    justify-content: center;
    align-items: center;
    background-color: white;
    padding: 10px;

    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
}

input[type="text"] {
    padding: 8px 12px;
    font-size: 16px;
    border: 1px solid #ccc;
    border-radius: 8px;
    outline: none;
    width: 250px;
}

input[type="text"]:focus {
    border-color: black;
}

button {
    padding: 8px 12px;
    font-size: 16px;
    margin-left: 10px;
    background-color: black;
    color: white;
    border: none;
    cursor: pointer;
}

button:hover {
    background-color: #0056b3;
}
</style>