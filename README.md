# React Animation
## What Are We Building?

we'll build a simple to-do app in React and animate it with React Transition Group and react-motion.

## Code the To-Do App

1. first check copy the 1st-CssToWrite.md to the index.css to start to have a basic style of our TODO App Compoennt.
2. create the App Component that will render and return the following jsx code
ex:
`<div className="container">
                <h1 className="todo-heading">To-dos</h1>
                <ul className="todo-list">
                <li className="todo-list__item">Item #1</li>
                <li className="todo-list__item">Item #2</li>
                <li className="todo-list__item">Item #3</li>
                </ul>
                <div className="todo-controls">
                <form>
                    <input 
                        className="todo-controls__input"
                        onChange="the handle add to do change"
                        placeholder="Add a todo"
                        type="text"
                        value="the new to do value"
                    />
                </form>
                <button className="todo-controls__button">Add</button>
                </div>
                </div>`

3. create a constructor for the app component with a props parameter , don't forget to call the super method with the props parameter
4. in the constructor create a state that have an empty array of todos (todos:[]), since you are using super, you should use this.
5. creaete a new method after the constructor method name it handleAddTodoCahnge(e), the idea of this method is to set the state newTodo: e.target.value
6. since you created a method to handle, normally you need to assign this method for the current component state using the bind method.
ex: this.handleAddTodoChange = this.handleAddTodoChange.bind(thid);

7. now you can attach the handle to the input (add a todo) with the method onChange (it is a compoent with a super so this is required also {})
8. create a handleSubmit(e) method and attach it to the form onSubmit (don't forget to bind the method it is a rule of thumb in react).
9. in the handleSubmit prevent the default action and let todos = this.state.todos; also push it to the newTodo (todos.push(this.state.newTodo)). at the end setStes by clearing newTodo and displaying todos.
10. create a getTodos() function that will return this.state.todos.map((todo,index) => {
    return (
        <li className="todo-list__item" key={todo.id}>{todo.text}</li>
    );
})
dont' forget to bind the method.
and replace the foollong code in the render return from 
`<li className="todo-list__item">Item #1</li>
                <li className="todo-list__item">Item #2</li>
                <li className="todo-list__item">Item #3</li>`

to
{this.getTodos()}
make sure you add the following const before the app component 
const uuid = require('uuid/v4');
this is a third party dependency that will generate an id for each todo list dynamically (like a GUID ID in dot net).

11. overwrite your index.css by copy and paste all content in the 2nd-CssToWrite.md file located at the root of react-animation folder.
12. update the default state of the app component by adding the uuid by default same as this example.
ex: 
todos: [
                {
                    id: uuid(),
                    text: 'Buy milk',
                },
                {
                    id: uuid(),
                    text: 'Return library book'
                },
                {
                    id: uuid(),
                    text: 'Think about life'
                }
            ]
13. in the nadlesubmit method fix the todos.push method to handle the uuid as following
ex:
let todos = this.state.todos,
            newTodo = {
                id: uuid(),
                text: this.state.newTodo
            };

        todos.push(newTodo);

## Animation using React Transition Group

React Transition Group is an animation add-on for React.
https://reactjs.org/docs/animation.html and https://github.com/reactjs/react-transition-group
1. You need to make sure that the dependency is installed using npm install react-transition-group --save (already installed on the packages)
2. then you need to import it in the app component import CSSTransitionGroup from 'react-transition-group/CSSTransitionGroup';

3. between `<h1 className="todo-heading">To-dos</h1>` and `<div className="todo-controls">`
add the following CSSTransitionGroup

`<CSSTransitionGroup
                    component="ul"
                    className="todo-list"
                    transitionName="new-todo"
                    transitionEnterTimeout={500}
                    transitionLeaveTimeout={500}
                >
                    { todos }
                </CSSTransitionGroup>`
you can set the todos as let todos = let todos = this.getTodos();

4. inspect the element and see what is happening in the DOM.
5. add the 3rd-CssToWrite.md to the index.css 


### Adding a delete checkbox

1. add the following input box in the getTodos method after {todo.text} `<input
                                className="todo-list__checkbox"
                                onChange={ () => this.handleRemove(todo.id) }
                                type="checkbox"
                            />`
and copy paste the related css on the 4rth-cssToWrite.md
2. create a handleRemove(id) that will let the newItems = this state todos filter((todo) => { return todo.id !== id });
3. set the state todos : new Items
4. check the DOM behavior while removing an item.
5. add the 5th-CssToWrite.md
                

## The React-motion Library

The techniques we’ve seen so far work great for simple effects, but for more complicated animations we can step up to the react-motion library. In this lesson I’ll teach you how it works and how we can integrate it into our to-do app.
https://github.com/chenglou/react-motion

1. You need to make sure that the dependency is installed.  npm install --save react-motion (already installed for you in the package)
2. import the library to our application component import Motion , spring, presets from react-motion
3. make sure that getTodos() is returning the following
ex:
`<Motion defaultStyle={{left: -1000}} style={{left: spring(0, presets.gentle)}} key={todo.id}>
                    {interpolatingStyle => (
                        <li
                            className="todo-list__item"
                            key={todo.id}
                            ref={item => { this[todo.id] = item }}
                            style={interpolatingStyle}
                        >
                            <span>{todo.text}</span>
                            <input
                                className="todo-list__checkbox"
                                onChange={ () => this.handleRemove(todo.id) }
                                type="checkbox"
                            />
                        </li>
                    )}
                </Motion>`

4. explaing the defaultStyle , and the style, and the pring with presets


