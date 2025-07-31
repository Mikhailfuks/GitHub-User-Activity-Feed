// script.js

document.getElementById('fetch-btn').addEventListener('click', fetchActivity);

async function fetchActivity() {
  const username = document.getElementById('username').value;
  const activityFeed = document.getElementById('activity-feed');

  // Clear previous activity
  activityFeed.innerHTML = '';

  if (!username) {
    alert('Please enter a GitHub username.');
    return;
  }

  try {
    // Fetch the user's events from GitHub API
    const response = await fetch(`https://api.github.com/users/${username}/events`, {
      method: 'GET',
      headers: {
        'Authorization': 'token YOUR_PERSONAL_ACCESS_TOKEN', // Replace with your token
        'Accept': 'application/vnd.github.v3+json'
      }
    });

    // Check if the response is okay
    if (!response.ok) {
      throw new Error('User not found or invalid username.');
    }

    const events = await response.json();

    // Display activity in the DOM
    events.forEach(event => {
      const activityItem = document.createElement('div');
      activityItem.classList.add('activity-item');











<!DOCTYPE html>
<html lang="en">

<head>
	<meta charset="UTF-8">
	<meta name="viewport" content="width=device-width, initial-scale=1.0">
	<title>GitHub User Activity Feed</title>
	<link rel="stylesheet" href="styles.css">
</head>

<body>
	<h1>GitHub User Activity Feed</h1>
	<input type="text" id="username" placeholder="Enter GitHub username" />
	<button id="fetch-btn">Fetch Activity</button>
	<div id="activity-feed" class="activity-feed"></div>

	<script src="script.js"></script>
</body>

</html>




















/* styles.css */

body {
    font-family: Arial, sans-serif;
    text-align: center;
    margin: 0;
    padding: 20px;
    background-color: #f4f4f4;
}

h1 {
    margin-bottom: 20px;
}

input[type="text"] {
    padding: 10px;
    width: 300px;
    border: 1px solid #ccc;
    border-radius: 5px;
    margin-right: 5px;
}

button {
    padding: 10px 20px;
    border: none;
    border-radius: 5px;
    background-color: #007bff;
    color: white;
    cursor: pointer;
    font-size: 16px;
}

button:hover {
    background-color: #0056b3;
}

.activity-feed {
    margin-top: 20px;
    text-align: left;
    max-width: 600px;
    margin-left: auto;
    margin-right: auto;
    background-color: white;
    padding: 10px;
    border-radius: 5px;
    box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
}

.activity-item {
    border-bottom: 1px solid #ddd;
    padding: 10px 0;
}

.activity-item:last-child {
    border-bottom: none;
}







