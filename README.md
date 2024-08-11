# // Lesson #4 - The Query Selector

```javascript
var books = document.querySelector("#book-list li .name");
console.log(books);

books = document.querySelectorAll("#book-list li .name");
console.log(books);

// turn boos variable into an array, iterate through it.
Array.from(books).forEach(function(book) {
  console.log(book)
}) 
```

# // Lesson #5 - Changing Text & HTML Content

```javascript 
var books = document.querySelectorAll("#book-list li .name");

// retrieve text content
Array.from(books).forEach(function(book) {
  // console.log(book.textContent)
})

// modify text content
Array.from(books).forEach(function(book) {
  book.textContent = "modified-text"
  console.log(book.textContent);
})

// append text content
Array.from(books).forEach(function(book) {
  book.textContent += " (modified-text)"
  console.log(book.textContent);
})

// displays the HTML content of an element
const bookList = document.querySelector("#book-list")
console.log(bookList.innerHTML)

// displays the HTML content of an element
bookList = document.querySelector("#book-list")
bookList.innerHTML = "<h2>Modified book content of the DOM</h2>";
bookList.innerHTML += "<p>This is how you append html...</p>";
```

# // Lesson #6 - Nodes

```javascript
const banner = document.querySelector("#page-banner");

// checking the node element methods 
console.log("#page-banner node type is:", banner.nodeType);   //the type
console.log("#page-banner node name is:", banner.nodeName);   // the name
console.log("#page-banner has child nodes:", banner.hasChildNodes());   //if element has child nodes

// to clone a node
const clonedBanner = banner.cloneNode(true);
console.log(clonedBanner)
```
# // Lesson #7 - Traversing the DOM (1)

```javascript
const bookList = document.querySelector("#book-list")

// find the parent node of an element
console.log("the parent node is:", bookList.parentNode)
// or we could use:
console.log("the parent element is:", bookList.parentElement.parentElement)   //finding the parent element of that parent element

// find all the child nodes
console.log(bookList.childNodes);   //gets even the line-breaks
console.log(bookList.children);   //only gets the children
```

# // Lesson #8 - Traversing the DOM (2)

```javascript
const bookList = document.querySelector("#book-list")

// to get the next sibling/element
console.log("book-list next sibling is:", bookList.nextSibling)
console.log("book-list next element sibling is:", bookList.nextElementSibling)

// to get the previous sibling/element
console.log("book-list previous sibling is:", bookList.previousSibling)
console.log("book-list previous element sibling is:", bookList.previousElementSibling)
```

# // Lesson #9 - Events

```javascript
var h2 = document.querySelector("#book-list h2");

// add an event listener to h2 tag
h2.addEventListener("click", function (e) {
  console.log(e.target);
  console.log(e);
});

var btns = document.querySelector("#book-list .delete");

// turn buttons into an array to loop through them
Array.from(btns).forEach(function(btn) {    //you can also use buttons.forEach without turning the buttons into an array.
  btn.addEventListener("click", function(e) {

    //when button is clicked we want to remove the li tag
    const li = e.target.parentElement;
    li.parentNode.removeChild(li)
  });
});
```

# // Lesson #10 - Event Bubbling

```javascript
const list = document.querySelector("#book-list ul")

// delete books by targeting delete element through the parent element
list.addEventListener("click", function(e){
  if(e.target.className == "delete"){
    const li = e.target.parentElement;
    list.removeChild(li);
  }
})
```

# // Lesson #11 - Interacting With Forms

```javascript
const addForm = document.forms["add-book"]

//prevents default form behavior, and select value of type input
addForm.addEventListener("submit", function(e) {
  e.preventDefault();
  const value = addForm.querySelector("input[type='text']").value;
  console.log(value)
})
```

# // Lesson #12 - Creating Elements

```javascript
const addForm = document.forms["add-book"]

addForm.addEventListener("submit", function(e) {
  e.preventDefault();
  const value = addForm.querySelector("input[type='text']").value;

  // lesson #12 create elements
  const li = document.createElement("li");
  const bookName = document.createElement("span");
  const deleteBtn = document.createElement("span");

  // add content to DOM
  deleteBtn.textContent = "delete";
  bookName.textContent = value;

  // append to the DOM
  li.appendChild(bookName);
  li.appendChild(deleteBtn);
  list.appendChild(li)
})
```

# // Lesson #13 - Styles and Classes

```javascript
const addForm = document.forms["add-book"]

addForm.addEventListener("submit", function(e) {
  e.preventDefault();
  const value = addForm.querySelector("input[type='text']").value;

  // lesson #12 create elements
  const li = document.createElement("li");
  const bookName = document.createElement("span");
  const deleteBtn = document.createElement("span");

  // add content to DOM
  deleteBtn.textContent = "delete";
  bookName.textContent = value;

  // lesson #13 styles and classes
  bookName.classList.add("name");
  deleteBtn.classList.add("delete");

  // append to the DOM
  li.appendChild(bookName);
  li.appendChild(deleteBtn);
  list.appendChild(li);
})
```

# //Lesson 14 - Attributes

```javascript
var book = document.querySelector("li:first-child.name")

// check attribute
book.hasAttribute("class");
book.hasAttribute("href");

// get attribute
book.getAttribute("class")
book.getAttribute("href")

// set attribute
book.setAttribute("class", "sector-O")

//remove attribute
book.removeAttribute("class")
```

# //Lesson 16 - Checkbox and Change Events
```javascript
const list = document.querySelector("#book-list ul");

// hide books
const toggle = document.querySelector("#hide");

toggle.addEventListener("change", function(e) {
  if(toggle.checked) {
    list.style.display = "none";
  } else {
    list.style.display = "block";
  }
});
```

# //Lesson 16 - Custom Search Filter

```javascript
const list = document.querySelector("#book-list ul");

// filter books
const searchBar = document.forms["search-books"].querySelector("input");
// keyup is an event listener
searchBar.addEventListener("keyup", function (e) {
  const term = e.target.value.toLowerCase();
  const books = list.getElementsByTagName("li");
  Array.from(books).forEach(function (book) {
    const title = book.firstElementChild.textContent;
    // condition
    if (title.toLowerCase().indexOf(term) != -1) {
      book.style.display = "block";
    } else {
      book.style.display = "none";
    }
  });
});
```
# //Lesson 17 - Tabbed Content

# //Lesson 18 - DOMContentLoaded Event

```javascript
// if the script tags in the HTML file are not placed within the body, but are placed within the head do this to make your javascript work.
document.addEventListener("DOMContentLoaded", function() {
  // put in all your written javascript here
})
```
