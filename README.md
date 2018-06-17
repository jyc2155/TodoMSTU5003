# TINKER - Javascript Part II

by Janet Choe, Caroline Moore, Xueling Chen, Xiao xiao Wang

## Tinker Tasks
Forked collab codepen - https://codepen.io/jyc2155/collab/Qxvzmw/

### Part 0: Conceptual Program Overview

Play with the program and observe how it reacts to user interactions.

- _Without_ talking about it in _programming terms_ explain the user observable steps/process of the following three interactions and how the program responds.
  :::info
  - Adding a todo: type in a todo and it will show on the list.
  - Completing a todo: when clicking on the circle/the text itself, the item completed will be grayed and crossed out.
  - Removing a todo(s):the completed todos will be removed (crossed out todos)
  :::

- For each of the interactions above write in _pseudocode_ the steps of how the program for that interaction unfold and results. Pseudocode is semi-formal structure to write out the gist of how your program would work. It uses some keywords but is largely language agnostic. There isn't a single correct way to do it but the following are some rules that can help.
  - RULES:
    - One statement per line
    - CAPITALIZE initial _keywords_
      - READ, WRITE, IF, ELSE, REPEAT, UNTIL, AND, OR
    - Indent to show hierarchy and groups of operation
    - Keep statements language independent

  ```markdown=
  # Making toast for a big family
  READ loaf of bread
  READ slide of loaf
    Put slice in toaster
      WRITE time to toast
      Start the toaster
        Cook the toast
          READ time
          WRITE time by one second less
        REPEAT UNTIL time is zero
    Remove toast
  REPEAT for all slices in loaf

  # Serving toast
  WRITE number of slices total
  READ number of family members
  READ toastiness
  IF toast is burnt AND (total slices >= number of family members)
    throw away toast
    decrement slices total
  ELSE
    serve toast to family member
  ```
- Using your pseudocode, identify the function(s) in the actual JS code that relate to your pseudocode.
  - Compare and contrast your pseudocode with the actual code.
  - Explain what similarities and differences you noticed about the instructions / steps / processes in the code vs. your psuedocode.
  :::info
    - Code and pseudocode is similar in the sense that it helps you guide through your code step by step. However, pseudocode are much more general than code because code is where we actually write multiple functions and codes to make the program work while pseudocode is like the general outline of what we want to accomplish/goal.  
  :::

### Part 1: Variables, Functions, Arrays, and Events

- Explain the `data` variable.
  - What does this data (and the data inside) represent conceptually?
  :::info
  - Data is an array of different objects. The objects represent the choices, which are the things that people need to do.
  :::
  - If I wanted to access the second object, how would I do that in code?
  :::info
  - `javascript = data[2]`
  :::
  - If I wanted to access the `done` property of the first object, how would I do that?
  :::info
  - `javascript= data[1].done`
  :::
- Look through the rest of the code where this `data` array is used. When the user does things, am I manipulating the visual display and updating the data to reflect those changes? Or am I manipulating the data and updating the visual display to reflect those changes?
	:::info
	 - The coder is manipulating visual display and updating the data the users has input. We think using this method helps the coder/s  change and find specific functions 
	:::


- What do these lines in my code do?
    ```javascript=
    var todosEl = document.querySelector('#todos');
    var inputEl = document.querySelector('input');
    var completedEl = document.querySelector('#counter');
    ```
    :::info
    -  read and store variables with the corresponding Id
    :::
- Why declare these (see above) variables at the Global scope instead of in the functions?
  :::info
  - So that we can recall these variables again instead of declaring variables again and again.
  :::
- The `toggleComplete` function has an event parameter. Inside the function I access `event.currentTarget`. What is the difference between `event.currentTarget` and `event.target` which we used previously?
  :::info
  - We think the difference is `event.target` is refering to the whole function while `event.currentTarget` is refering to what is passed in the function.
   :::

- In the `toggleComplete` function, there is a `event.currentTarget.id`. Is that `id` the same thing as the id property in my todo objects in the `data` array?
  :::info
  - Yes they are the same. But if the user input new todo, it will probably change
  :::
  
- What does `!something` mean? (The exclamation mark) and how is it used in this code when we `toggleComplete`?
  :::info
  - `todoData.done = !todoData.done;` This is a Boolean when True becomes False and vice versa.
  - This is applicable to Boolean data which are ‘TRUE’ or ‘FALSE’. In toggleComplete, with each click,	todoData.done = !todoData.done; and the state of todoData.done will change.
  :::
- Try calling some of the functions directly from the console. Some will work. Some won't.
  :::info
  - `toggleComplete()` did not work because there is no event happening/ event is undefined.
  :::
- Use the console (in Chrome devtools) to `console.log()` and `console.dir()` the following. What is the difference between `console.log` and `console.dir` and why is `console.dir` kind of more useful for looking at some kinds of data?
    ```javascript=
    console.log(data);
    console.log(todosEl);

    console.dir(data);
    console.dir(todosEl);
    ```
  :::info
  - `console.log` prints out the content of the argument passed into it. 
  - `console.dir` logs an interactive listing of an object’s properties. By console.dir we can quickly identify the property of the object and thereby by these properties to select the element.
  :::

### Part 2: Objects and Arrays of Objects

- Manipulate the different _properties_ of the _objects_ inside the `data` array.
  - Change all todo objects' `done` property to `true`.
  - Change some of the task values.
  - Run your code and explain how this changes what you see and why.

- `console.dir()` the `data` array. Goto the console and _OPEN_ the `> Array(3)` text by clicking on it. Go deeper by opening up the nested objects. Analyze what you see. Then add a new todo through the user interface. `console.dir()` the `data` array again and investigate the insides.
  - What is the difference between `data` before and after adding a new todo?

- Run the following code:
    ```javascript=
    data.push({
      done: true,
      task: "Goto Aikido Lessons",
      id: getTimeStamp()
    });
    console.dir(data);
    ```
  - What did the code above do?
  - Does our page reflect the changes made? Why or why not? Prove it.
  - Does order matter in `Objects`?

- What is the difference between `Object` keys (E.g. `done`, `task`, `id`) and `Array` indices (E.g. `0`, `1`, `2`)?
  - How are they similar?
  ```javascript=
  var myAry = [123, "Code", true];
  var myObj = {
    id: 123,
    task: "Code",
    done: true
  }
  console.log(myAry[1]);
  console.log(myObj["task"]);
  console.log(myObj.task);
  ```

- Compare the following in the console:
  ```javascript=
  var element = document.querySelector('ul');
  var author = { first: "Mark", last: "Twain" }

  var example = {
    theAnswer: 42,
    student: true,
    hobby: "Fishing",
    sayHello: function(){
      alert("Hello");
    },
    favNums: [1,2,3],
    favAuthor: author
  };

  console.dir(example);
  console.dir(el);
  ```
  - What is an `element` really?
  - How does our `element` relate in terms of similarities and differences to `example`?
  - If I wanted to call the function in the `example` object, how would I do that? Prove it.

- Try the following code in the console. How does dot notation and bracket notation differ and why would you want to use one or the other?
  ```javascript=
  var x = "username";
  var user = {
    username: "happyCat"
  }
  console.log(user.username);
  console.log(user["username"]);
  console.log(user[x]);
  console.log(user.x);
  ```
- Identify various areas where the `.` object notation is used and explain the thing on the left side of the `.` and the thing on the right side of the `.`
  - E.g. `document.querySelector()` `document` is... `querySelector` is...
  - HINT: There are MANY choices here.

- In two areas of my code, I use what is called a `filter` function. It's a function that arrays can use like `list.pop()`, `list.push()`.
  - How does a filter function work?
  - What is the significance of the function argument that is passed INTO the filter parameters?
  - With regard to the function that is passed into the filter as an argument, that function must `return` a boolean or evaluate to a boolean. What is the purpose of this?
  - What does the _filter function_ return?
    E.g. `var x = list.filter(...); // What was returned to x?`
    - CAUTION: NOT the function argument that goes into the filter.
    - HINT: If you don't know, can you use console to "test" an idea out?
  - Does filtering an array _change_ the original array?

### Part 3 Control Structures

- I use the `if` statement in several places in this code. Explain why a conditional is necessary in:
  - `updateTodoItems`
  - `updateRemoveButton`
  - `onEnterKey`
  - `validateTask`
  - `addTodoItem`
  - `getTodoData`
  - HINT: You might want to `console.log` the boolean condition where you see the `if` statements to understand what condition we are evaluating.
  ```javascript=
  if (booleanCondition) {
    ...
  }
  console.log(booleanCondition);
  ```
  - Comment on how the boolean condition works as there are many different examples.
   :::info
  - A conditional is necessary in each of these functions because they rely on checking the status of the content in order to activate late items. For example, with `validateTask` the function must check to make sure the contents aren't empty before allowing a todo item to be added. This is also important with many of them, as the first conditional stops the function from completing if there are no elements that fufill their requirements (i.e. `getTodoData`, `updateRemoveButton`) or allow for other forms of "clicking" such as in `onEnterKey`. The boolean condition runs first to determine if a condition is false and then proceeds or stops depending on the result.
   :::

- In this code, there are two kinds of `for` loops. The more traditional that looks like:

    ```javascript=
    for (var i=0; i < list.length; i++) {
      // CODE
    }
    ```
    and a `for of` loop that looks like:
    ```javascript=
    for (item of list) {
      // CODE
    }
    ```
  - How does a `for of` loop work?
    - What does the `item` represent? (It can be named anything: `x`, `item`, `thing` etc.)
  - Why are `for of` loops convenient compared to the traditional `for`?
  - For what purpose(s) do I employ a `for` or `for of` loop in this program?
  :::info
  - A for of loop sets a set or range of items on which the next conditions act, thus limiting the active sections of the code for that function. The `item` represents the specific variables that are being selected.
  - `for of` loops are convenient in that it specifies out a particular item independent of order and can take any type of items that can be listed. It also gives more easily determined instructions to find the data and keeps the code tidy and easy to read. 
  :::
  - On Facebook or Pinterest, or Twitter, how does a loop through data relate to the display of content?
  :::info
  - The content on social media platforms is personalized, thus for loops will read the preferences/likes/friends etc of the user in order to display specific data. It is a good way of iterating what to show based on various variables.
  :::

### Part 3 Specific Routines

- Take a look at the `updateTodoItems`. Comment it out and replace it with this alternate, but functionally identical version. How does this function work and how do they relate / differ?
```javscript=
function updateTodoItems() {
  todosEl.innerHTML = "";

  if (!data.length) {
    var liElement = document.createElement('li');
    liElement.innerText = "Nothing todo...";
    todosEl.appendChild(liElement);
  } else {

    for (todo of data) {
      var liElement = document.createElement('li');
      var iElement = document.createElement('i');

      liElement.id = todo.id;
      liElement.onclick = toggleComplete;

      if (todo.done) {
        liElement.className = "complete";
        iElement.className = "fa fa-check-circle-o";
      } else {
        iElement.className = "fa fa-circle-o";
      }

      liElement.appendChild(iElement);
      liElement.innerText = todo.task;

      todosEl.appendChild(liElement);
    }
  }

  updateRemoveBtn();
}
```
:::info
- This section functions basically same, but doesn't have the checkbox element to click, so perhaps isn't as intuitive to the user. The code itself is easier to read without the elements that control the circular checkmarks.
:::

- Take a look at the helper function `getTimeStamp`. This function will return a number, in milliseconds, the current time stamp since January 1, 1970.
  - I call this when I create new todo items, what are some ideas as to why I might be using a timestamp for todo `ids`?
 :::info
 - Using the time stamp in milliseconds gives each element a completely unique id (which is necessary within the code to access specific element). It is practically impossible to get the same exact id using this method. 
 - This could also let you later access the date you wrote it and the date you completed it to provide more information to the user about completion time if that portion of the code is written
 :::

- Take a look at the incomplete functions `markAllComplete` and `updateItemsLeft`.
  - Can you complete these and add the functionality to this app?
 :::info
 - We were able to get this working by looking at functions from earlier interactions and applying similar code to these ones. They function as long as they are called in the beginning for `updateItemsLeft()` (which was an issue we had to figure out when it wasn't working...) 

```javascript=
function markAllComplete() {
    for (var i=0; i < data.length; i++) {
      data[i].done = true;
    }
    updateTodoItems();
}

function updateItemsLeft() {
	var incompleteTodos = data.filter(function(todo){
	  return todo.done === false;
	});
  incompleteEl.textContent = incompleteTodos.length;
}
```
 :::

### Part 4 Debugging, Tools

Using the Chrome debugger (source) tool create breakpoints and watch the program execute line by line, part by part. Experience how this tool can give you insight into your program's _STATE_, _SEQUENCE_, _CAUSALITY_.

#### Chrome Debugger

- Set breakpoints at the following locations of your program
  - `function initializeTodos`
  - `function onEnterKey`
  - `function addTodoItem`
  - `function toggleComplete`

- Use the `Step over the next function call` feature to watch how the program pauses during the _SEQUENCE_ of its routines.
- Use the `Step into the next function call` feature to watch how the program pauses during the _SEQUENCE_ of its routines.
  - What is the difference between `Step over` and `Step into` and how does this help you understand programs?
:::info
step over: Executes whatever happens on the next line and jumps to the next line.
step into: If the next line contains a function call, Step Into will jump to and pause that function at its first line; it ensures that only one statement gets executed, no matter what functions you step in and out of.
:::
- Use `Step into` until you've reached the line `var inputEl = document.querySelector('input');`. Should be highlighted in blue.
  - Highlight the variable `todosEl` on the line before it and `right click` on it. Select _Evaluate in console_.
    - What does the console print?
:::info

:::

  - Highlight the variable `inputEl` on this highlighted blue line.
    - Why does the console say `inputEl` is undefined?
    - When you step through your code, does the blue line represent code that is about to be executed or code that has already executed? How do you know?
    - What do you predict would be the console value of the variable `completedEl` on the next line if you _Evaluate to console_ at this point?
- Watch how debugger annotates your source code with the updated _state_ of different variables as your program progresses.
  - How does the debugger behave when you enter a loop in your program?
  - How does the debugger behave when you reach the a `filter` function call?
  - What does filter do and how does it work?


### Part X: Putting all together

**Explain the program line by line with sufficient details, part by part.**
:::success
- Line by line
  - Part by part
- Be sure to copy blocks of code into this markdown using code formatting/fences as references to your explanations.
- For repetitive code, you can explain how a line works then summarize how it would work for the rest.
:::
```javascript=
var data = [
	{
		id: 1497141891479,
		task: "Wake up",
		done: false
	},
	{
		id: 1497141913701,
		task: "Eat breakfast",
		done: false
	},
	{
		id: 1497141937545,
		task: "Learn code",
		done: true
	}
];
// Important Elements - Cached as variables
var todosEl = document.querySelector('#todos');
var inputEl = document.querySelector('input');
var completedEl = document.querySelector('#counter');
```
^Define the data array. Each item has three obect key. Id updateitem and remove function; Task the content of the to-do list item and the value of input.Done decides the state of list item (whether it is in complete class or not).

Global variables assigned to specific HTML elements so that the coder can call those variables anywehre in the code.

```javascript=
function initializeTodos() {
	updateTodoItems();
}


function updateTodoItems() {
	var todosHTML = "";
	for (todo of data) {
		if (todo.done) {
			todosHTML += `<li id="${ todo.id }" class="complete" onclick="toggleComplete(event)">`;
			todosHTML += `<i class="fa fa-check-circle-o"></i>`; // Font-awesome
		} else {
			todosHTML += `<li id="${ todo.id }" onclick="toggleComplete(event)">`;
			todosHTML += `<i class="fa fa-circle-o"></i>`; // Font-awesome
		}

		todosHTML += `${ todo.task }`;
		todosHTML += `</li>`;
	}
	if (todosHTML === "") {
		todosHTML = "<li>Nothing todo...</li>";
	}
	todosEl.innerHTML = todosHTML;
	updateRemoveBtn();
}
```
^When the program starts, the function initalizeTodoItems is called which calls the next function updateTodoItems() which is the function that triggers when users add a to do item. The program than add what userinput to the array. Then calls another function called updateRemoveBtn().

```javascript=
function updateRemoveBtn() {
	var completedTodos = data.filter(function(todo){
	  return todo.done === true;
	});

	completedEl.textContent = completedTodos.length;

	if (completedTodos.length) {
		completedEl.parentElement.disabled = false;
	} else {
		completedEl.parentElement.disabled = true;
	}
}
```
^Return all the items whose object key 'done' is true and add them to completeTodos array.Show the number of objects inside this new list in the `Remove` button. If the array length is 0, the `remove` button will be disabled and cannot be clicked.
```javascript=
function onEnterKey(event) {
	if (event.code === "Enter") {
		addTodoItem();
	}
}
```
^When the user press 'enter key', addTodoItem() funciton is triggered.
```javascript=
function validateTask(task) {
	if (task !== "") {
		return true;
	} else {
		return false;
	}
}

```
^ When something is inputted, this function determines whether or not it has content. If the new task is not empty, it returns true, otherwise it returns false and is deemed not valid. 
```javascript=
function addTodoItem() {
	if (!validateTask(inputEl.value)) {
		return;
	}
var newTodo = {
		id: getTimeStamp()
	};

	newTodo.task = inputEl.value;
	newTodo.done = false;

	data.push(newTodo);

	updateTodoItems();
	resetInput();
}
```
^Sets the function to add a todo item with the value of the input unless it fails the validation function which stops the function. The code then sets a variable for a new todo item with the id set as the result of the `getTimeStamp()` function (see later in the code description). The next lines set the `task` of the new variable to the value that was inputed and then sets its default state to being unfinished. It then adds the  `newTodo` variable to the end of the data array and calls for the code to run `updateTodoItems()` and resets the input via `resetInput()`
```javascript=
function toggleComplete(event) {
	var todoID = parseInt(event.currentTarget.id);
	var todoData = getTodoData(todoID);
	todoData.done = !todoData.done;
	updateTodoItems();
}
```
^The function with the event lets the circular check box be clickable and trigger the event contents. It sets the variable `todoID` as the converted string of the target's id and the variabla `todoData` as the data of that previously set id (see later function definition). This then allows the function to change the state of the "done" portion of the data to whatever is the opposite (triggering the check vs unchecked) in the true/false boolean that occurs there.
```javascript=
function removeTodoItem(event) {
	var incompleteTodos = data.filter(function(todo){
	  return todo.done === false;
	});
	data = incompleteTodos;
	updateTodoItems();
}
```
^Function that runs when the remove button is clicked. The variable `incompleteTodos` is set to a filter to the data that runs a function that only returns the todo elements whose "done" portions returns false. The functin then sets the data array to the result of that and runs a function to update the HTML to only those elements.
