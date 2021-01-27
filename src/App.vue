<template>
    <h1> Simple Todolist using VUE! </h1>
    <p> 
        This is a little project I worked on to test out the functionality of Vue.
        It showed me the strengths of the framework and am excited to continue working with it.
        I hope that I can make solid entireprise level projects with this in the future, it also opened 
        my eyes to frameworks such as React and Angular.
    </p>
    <TodoList></TodoList>
    <i> 
        NOTE: Write a todo and click on "Add todo" or press enter to get a new todo added. 
        If you want to check a todo off without deleting it press the ":(", Goodluck!
    </i>
</template>

<script>
    import TodoList from './components/TodoList.vue'

    export default {
        name: 'App',
        components: {
            TodoList
        }
    }
</script>
