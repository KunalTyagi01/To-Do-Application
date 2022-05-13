# To-Do-Application

# Part-1 HTML

To summarise, we add meta tags, the link tag for connecting the document to the style.css file, and the script (which allows us to retrieve an icon from fontawsome.com) in the head section. We'll only use the trash can icon and the title in this example.

Then there are two sections in the body: header and ul. A h1 headline appears in the header element, and below it is a text input element allowing the user to enter ToDo items, as well as a button to get the input values. There is an empty ul element behind the header. When we receive input from the user, we will show the input items in li elements here.
At the end of the body> section, we use the script tag to link to the Javascript file.


# Part-2 CSS

First, We use Google Fonts to import the "Titillium Web" font style. The header and the h1 title are then styled. We may pull the code and arrange the linear gradient colours. I utilised the same font style, size, and padding values for the input element and the "Add" button to make both elements similar height. The duration of the style change from normal to hover is set by the transition value at the "Add" button.

We've styled the visible elements up to this point. Now we'll set the design for elements that don't exist yet but will appear as user input comes in. These are simple li elements that carry the ToDo messages and other information. There is no need to label the li components with class or id because they should all look the same. That is why we utilise the ul li selector. To show the user that this is a clickable element, we first set the cursor to pointer.

After that, we change the position to relative. This is because we will add two items/icons as a child or as a before pseudo element, and we will position the icons in respect to the position of the components. Giving the child components absolute position is one method to achieve this. However, we must offer the parent element relative position in order for them to take position in relation to it.Again, the length of the style change from normal to hover is determined by the transition value. We prefer not to have the elements selectable by the user. As a result, we set the user-select attribute to none and add extra codes to ensure that this works in several browsers.

Now we'll use the before pseudo element to make the tick icon on the left. We're going to construct a vertical rectangle here. Then we applied a 2px border to only two sides, giving it the appearance of a mirrored letter "L." When we use the transform attribute to rotate the icon 45 degrees clockwise, we obtain an icon that looks exactly like a tick. Finally, we make the icon absolute to the parent element, so it appears at the start of the line.



# Part-3 Javascript

The fundamental structure we'll use in the JS section is to construct a class and then embed the methods within it. This signifies that a significant portion of the programme will execute within the class. We begin by creating a variable that contains an array of items. Every user input will be stored as an object in this array.Then we build the Todo Class class. The single parameter of the class is the ul element, which is where all of the JS action takes place. As a result, we'll build up procedures for:

The user input is added to the todoListObjectArray.
Changing the status of components from done to undone.
Delete components and show everything on the screen.

We'll get back to the class soon, but first, let's get to the meat of the script.

First, we assign the element to a "listSection" variable, which will be used as a parameter in the instance we'll generate. After that, we create our instance "myTodoList" from the "Todo Class" and set the parameter "listSection." The script is then started by assigning a click event to Add Button. Using the add() method inside the myTodoList instance, we can take user input and turn it into an object. Let's have a look inside the add() method to understand what's going on. To begin, we obtain the user input value in string format and apply it to the todoInput variable. However, we should check to see if the user simply clicked the add button without typing anything. Using an if statement is a pretty basic method. Give an alert if the input is an empty string; else, take the input. We choose to utilise an object with three properties: id, todoText, and isDone to hold the data. The length of the object array is assigned as id, which is a straightforward approach. Every time we add a new item, the id rises by one. isDone is a boolean that is false by default, and todoText is the same as the string type user input.

When the user clicks on the element, we'll change it to true. We add the first object to the object array when it is created. We used unshift() instead of push() because we wanted the most recent entries to appear first. It's now time to show off what we've got. And now that we know what the input value is, we can clear the input box so the user doesn't have to.

The most difficult component is probably Display(), but it's still not a big deal. The following line cleans the content of the element at the start. Because the algorithm here is that the approach develops material from beginning to end every time. If we don't clear in the start, we'll see the same items every time the user selects the add button. We now establish a forEach loop for each object item in the object array, and we perform multiple tasks within it. We begin by adding two new variables that will be used to generate elements for displaying the incoming data. The trash icon is represented by the I element. Now, for each delBtn element we construct, we add a click event listener that calls a method that deletes the selected object in the array and displays the remaining objects on the screen. We'll go over it when we finish with the display() method. The most crucial thing here is that we assign an item's id value to a variable called deleteId, but how do we do it? We get {n<i data-id=”0” class=”far fa-trash-alt”></i>} from e.target. (The id value will undoubtedly differ depending on whatever item in the object array we are on.) And we get the value of the data-id attribute using e.target.getAttribute("data-id"), which is 0 in this case. The deleteElement function takes the id value as an attribute. We add a click event to each liElement in the object array, get the same id value as before, and pass it to the done undone function as a parameter. We'll alter the isDone property there.

The display() method's final move. For each object in the object array (todoObjectList), we created a liElement and set the content and data-id attributes. However, because we have not specified the location where it should stay, it does not appear on the screen. We placed it as a child element of the ulElement below, so it now has a designated location and is ready to appear. Everything is done in a forEach loop, so each object in the loop is displayed on the screen and receives click events. The display() method is now complete. We can now concentrate on the done undone() method. Remember that we passed the object's id value as an argument to this method. We set the object's index number to the selectedTodoIndex variable, which has the same value as the inserted parameter's value. How? findIndex() retrieves the index value of a certain object element in an object list. Find the index number of a certain object in the todoObjectList with todoObjectList.findIndex(). However, in the parenthesis, we must specify what we are looking for. ((item)=> item.id == x) which implies we want to bring the item in the array whose id property value equals our parameter x, which is the id value of the liElement we got by clicking on it.

The delete method works similarly to the done undone method. In the same method, we get the index value. We utilise the splice method to acquire the id value to delete.


# And that's it!!!
