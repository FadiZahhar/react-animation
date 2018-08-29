* {
    box-sizing: border-box;
}

body {
    background: #e96443; /* fallback for old browsers */
    background: -webkit-linear-gradient(to left, #e96443 , #904e95); /* Chrome 10-25, Safari 5.1-6 */
    background: linear-gradient(to left, #e96443 , #904e95); /* W3C, IE 10+/ Edge, Firefox 16+, Chrome 26+, Opera 12+, Safari 7+ */
    margin: 0;
    padding: 0;
    font-family: sans-serif;
}

.container {
    margin: auto;
    width: 50%;
}

.todo-heading {
    color: whitesmoke;
    margin-bottom: 0;
}

.todo-list {
    list-style: none;
    margin-top: 0.5em;
    padding: 0;
}

.todo-list__item {
    background: rebeccapurple;
    color: white;
    margin-bottom: 1px;
    padding: 1em 2em;
    position: relative;
}

.todo-list__checkbox:hover {
    background: white;
}

.todo-controls {
    text-align: center;
}

.todo-controls__input {
    border: 0;
    font-size: 18px;
    padding: 0.5em;
    width: 100%;
}

.todo-controls__button {
    background: rebeccapurple;
    border: 0;
    color: white;
    font-size: 18px;
    margin: 0.5em 2em;
    padding: 0.5em 1em;
}

.todo-controls__button:hover {
    background: palevioletred;
    cursor: pointer;
}
