<script setup>
import { ref } from 'vue'

const itemId = ref(0)
const shoppingitem = ref('')
const shoppinglist = ref([])
const shopped = ref(false)

function addItem() {
    shoppinglist.value.push({
        id: itemId.value++,
        item: shoppingitem.value,
        status: shopped.value
    })

    shoppingitem.value = ""
}

function removeItem(i) {
    shoppinglist.value = shoppinglist.value.filter((t) => t !== i)
}


</script>
<template>

    <div class="myDiv">
    <h1>
            Todo App
        </h1>
        <input type="text" v-model="shoppingitem">
        <button @click="addItem">Add List</button>

        <ol>
        <li v-for="i in shoppinglist">
            <input type="checkbox" v-model="i.status">
            <span :class="{done: i.status}"> {{ i.item }}</span>
            <button @click="removeItem(i)">X</button>
        </li>
        <h5 v-if="shoppinglist.length < 1"> No List</h5>
        </ol>
    </div>

</template>

<style scoped>
.done {
    text-decoration: line-through;
}
.myDiv {
    border:5px outset rgb(0, 128, 92);
    background-color: rgb(41, 41, 41);
    text-align: center;
    padding: 60px;
}
</style>