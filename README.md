# 🎯 JavaScript Event Handling & Interactive Elements Assignment

Welcome to the **ultimate JavaScript playground**! 🎉 This assignment is where we turn boring web pages into dynamic, responsive, *alive* experiences. Get ready to master **event handling**, build **interactive components**, and validate forms like a pro! 💪

## 📁 Assignment Structure

```
📂 js-event-assignment/
├── index.html         # Your playground – where it all comes together
├── style.css          # Keep it cute (optional but encouraged)
└── script.js          # The JavaScript wizardry happens here
```

---

## 🧪 What to Build

Here’s what your interactive bundle of joy should include:

### 1. Event Handling 🎈  
- Button click ✅  
- Hover effects ✅  
- Keypress detection ✅  
- Bonus: A secret action for a *double-click* or *long press* 🤫

### 2. Interactive Elements 🎮  
- A button that changes text or color  
- An image gallery or slideshow  
- Tabs or accordion-style content  
- Bonus: Add some animation using JS or CSS ✨

### 3. Form Validation 📋✅  
- Required field checks  
- Email format validation  
- Password rules (e.g., min 8 characters)  
- Bonus: Real-time feedback while typing

---

## 🧙‍♂️ Pro Tips

- Keep your code clean and commented – your future self will thank you!
- Think about **user experience** – what makes your site more *fun* to use?
- Don’t be afraid to **Google and experiment** – that’s how real developers roll!

---

## 🎉 Now Go Make It Fun!

Remember – this isn't just code. It's your **first step toward creating magical user experiences**. So play around, break stuff (then fix it), and most of all, have FUN! 😄

Happy Coding! 💻✨ 

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Interactive JavaScript Playground</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <h1>JavaScript Event Handling & Interactive Elements</h1>

  <!-- Event Handling -->
  <button id="clickButton">Click Me!</button>
  <br><br>

  <button id="hoverButton">Hover Over Me!</button>
  <br><br>

  <input type="text" id="inputField" placeholder="Press a key...">
  <br><br>

  <button id="secretButton">Double-click me</button>
  <br><br>

  <!-- Interactive Elements -->
  <button id="changeButton">Click to Change Color and Text</button>
  <br><br>

  <div id="gallery">
    <img id="galleryImage" src="image1.jpg" alt="Gallery Image" width="300">
    <button id="nextImageButton">Next Image</button>
  </div>
  <br><br>

  <div class="tabs">
    <button class="tabButton" data-target="tab1">Tab 1</button>
    <button class="tabButton" data-target="tab2">Tab 2</button>
  </div>
  <div class="tabContent" id="tab1">Content for Tab 1</div>
  <div class="tabContent" id="tab2">Content for Tab 2</div>
  <br><br>

  <!-- Form Validation -->
  <form id="myForm">
    <input type="text" id="username" required placeholder="Username">
    <button type="submit">Submit</button>
  </form>
  <br><br>

  <form id="emailForm">
    <input type="email" id="email" placeholder="Enter email" required>
    <button type="submit">Submit</button>
  </form>
  <br><br>

  <form id="passwordForm">
    <input type="password" id="password" placeholder="Enter password" required>
    <button type="submit">Submit</button>
  </form>
  <br><br>

  <input type="password" id="passwordField" placeholder="Enter password">
  <p id="passwordFeedback"></p>
  
  <script src="script.js"></script>
</body>
</html>


/* Simple styling to make things look neat */
body {
  font-family: Arial, sans-serif;
  margin: 20px;
}

button {
  padding: 10px 15px;
  cursor: pointer;
  font-size: 16px;
}

button:hover {
  background-color: lightgray;
}

.tabContent {
  display: none;
}

#changeButton {
  transition: background-color 0.3s ease;
}

#changeButton {
  transition: transform 0.2s ease;
}

#changeButton.clicked {
  transform: scale(1.2);
}


// 1. Event Handling

// Button click
document.getElementById("clickButton").addEventListener("click", function() {
  alert("Button clicked!");
});

// Hover effects
const hoverButton = document.getElementById("hoverButton");
hoverButton.addEventListener("mouseover", function() {
  hoverButton.style.backgroundColor = "blue";
  hoverButton.style.color = "white";
});
hoverButton.addEventListener("mouseout", function() {
  hoverButton.style.backgroundColor = "";
  hoverButton.style.color = "";
});

// Keypress detection
document.getElementById("inputField").addEventListener("keypress", function(event) {
  alert("You pressed: " + event.key);
});

// Bonus: Double-click or Long Press action
document.getElementById("secretButton").addEventListener("dblclick", function() {
  alert("You found the secret action!");
});

// 2. Interactive Elements

// Button that changes text or color
document.getElementById("changeButton").addEventListener("click", function() {
  this.textContent = "Color Changed!";
  this.style.backgroundColor = "green";
});

// Image Gallery/Slideshow
const images = ["image1.jpg", "image2.jpg", "image3.jpg"];
let currentImageIndex = 0;
document.getElementById("nextImageButton").addEventListener("click", function() {
  currentImageIndex = (currentImageIndex + 1) % images.length;
  document.getElementById("galleryImage").src = images[currentImageIndex];
});

// Tabs or Accordion-style Content
const tabButtons = document.querySelectorAll(".tabButton");
const tabContents = document.querySelectorAll(".tabContent");

tabButtons.forEach(button => {
  button.addEventListener("click", function() {
    tabContents.forEach(content => content.style.display = "none");
    document.getElementById(button.dataset.target).style.display = "block";
  });
});

// 3. Form Validation

// Required field check
document.getElementById("myForm").addEventListener("submit", function(event) {
  const username = document.getElementById("username").value;
  if (username.trim() === "") {
    alert("Username is required!");
    event.preventDefault(); // Prevent form submission
  }
});

// Email format validation
document.getElementById("emailForm").addEventListener("submit", function(event) {
  const email = document.getElementById("email").value;
  const emailRegex = /^[\w-]+(\.[\w-]+)*@([\w-]+\.)+[a-zA-Z]{2,7}$/;
  if (!emailRegex.test(email)) {
    alert("Please enter a valid email address.");
    event.preventDefault();
  }
});

// Password strength validation (Min 8 characters)
document.getElementById("passwordForm").addEventListener("submit", function(event) {
  const password = document.getElementById("password").value;
  if (password.length < 8) {
    alert("Password must be at least 8 characters.");
    event.preventDefault();
  }
});

// Real-time feedback while typing
document.getElementById("passwordField").addEventListener("input", function() {
  const feedback = document.getElementById("passwordFeedback");
  if (this.value.length < 8) {
    feedback.textContent = "Password too short!";
    feedback.style.color = "red";
  } else {
    feedback.textContent = "Password is long enough!";
    feedback.style.color = "green";
  }
});

