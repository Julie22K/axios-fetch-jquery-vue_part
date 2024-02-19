<template>
    <div id="list" class="transision">
        <h3 class="font-bold">Студенти:</h3>
        <p class="text-gray-500 my-3 mx-2" v-if="!items">Дані завантажуються... </p>
        <ul class="decimal-list ml-8" v-for="item in items" :key="item.id">
            <li>{{ item.id }}. {{ item.first_name }} {{ item.last_name }}</li> 
        </ul>
        <button class="bg-sky-400 text-white p-2 m-2 cursor-pointer rounded-sm" id="openForm" @click="$emit('toggleFormAndList')">Додати студента</button>
    </div>
</template>

<script>
  export default {
    name: 'List',
    props: {
        items:Array
    }
  }
</script>

  
  