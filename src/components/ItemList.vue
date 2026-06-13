<!-- src/components/ItemList.vue -->
<!-- src/components/ItemList.vue -->
<script setup lang="ts">
import { ref } from 'vue'

interface Item { 
  name: string
  date: number
} 

const tasks = ref<Item[]>([  
]) 
const newItemName = ref('')
const limit = ref(0)
const addTask = () => {
    tasks.value.push({
        name: newItemName.value,date: limit.value
    })
}
const delateTask = (name: string) => {
    tasks.value = tasks.value.filter((tasks)=>tasks.name !== name)
}
</script>

<template>
  <div>ItemList</div>
  <ul>
    <li v-for="task in tasks" :key="task.name">
        <input type="checkbox" name="property" id="">
        <div>
            <span>タスク名: {{ task.name }}</span><br>
            <span>〆切:{{ task.date }}</span><br>
            <button @click="delateTask(task.name)">削除</button>
        </div>
        <!--<div>{{ task.price }} 円</div>-->
        <!--<div v-if="task.price >= 10000">高額商品</div>-->
    </li>
  </ul>
  <div>
    <label>
        名前
        <input v-model="newItemName" type="text" />
    </label>
    <label>
        〆切
        <input v-model="limit" type="text" />
    </label>
    <button @click="addTask">追加</button>
  </div>
</template>

<style>
.over500{
    color: red;
}
li{
    list-style: none;
}
li > input{
    float: left;
}
</style>