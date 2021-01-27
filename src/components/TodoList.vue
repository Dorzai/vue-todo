<template>
    <ul>
        <li> <button class="right" @click="DeleteAllItems()"> Delete All </button> </li> <br>
        <li v-for="item in list" :key="item.id"> 
            <span class="checkbox" :class="[!item.completed ? 'sad' : 'happy']" @click="ToggleCompleted(item)"> 
                <b v-if="!item.completed"> :( </b>
                <b v-if="item.completed"> :) </b>
            </span>  
            <span :class="[item.completed == false ? '' : 'line']"> {{ item.item }} </span>
            <button class="right" @click="DeleteItem(item)"> Delete </button>
        </li>
        <li> 
            <input type="text" placeholder="Insert todo.." v-model='newItem' @keyup.enter="AddItem()">
            <button class="add" @click="AddItem()" :disabled="newItem.length == ''"> Add todo </button>
        </li>
    </ul>
</template>

<script>
    export default {
        name: 'TodoList',
        data() {
            return {
                list: [
                    { id: 0, item: 'Make a doctors appointment.', completed: false },
                    { id: 1, item: 'Stay awake, and sleep early', completed: false },
                    { id: 2, item: 'Level up again in Maplestory', completed: false },
                    { id: 3, item: 'Find an adorable kitten to pet', completed: false },
                    { id: 4, item: 'Enjoy life, even during these times', completed: false }
                ],
                newItem: ''
            }
        },
        methods: {
            ToggleCompleted: function(item) {
                let itemIndex = this.list.indexOf(item);
                this.list[itemIndex].completed = this.list[itemIndex].completed == false ? true : false;
            },

            AddItem: function() {
                let newId = this.list[this.list.length - 1]?.id ?? 0;
                this.list.push({ id: newId, item: this.newItem, completed: false });
                this.newItem = '';
            },

            DeleteItem: function(item) {
                let itemIndex = this.list.indexOf(item);
                this.list.splice(itemIndex, 1);
            },

            DeleteAllItems: function() {
                this.list.splice(0);
            }
        }
    }
    </script>
