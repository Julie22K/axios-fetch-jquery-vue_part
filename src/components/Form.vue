<template>
    <div id="form" class="transision">
        <div class="flex flex-col">
            <legend class="font-bold">Додати студента</legend>
            <label for="first_name"></label>
            <input v-model="first_name" class="border rounded my-4" type="text" id="first_name" name="first_name">
            <label for="last_name"></label>
            <input v-model="last_name" class="border rounded my-4" type="text" id="last_name" name="last_name">
            <div class="flex w-full justify-between">
                <button class="w-20 cursor-pointer bg-green-400 text-white p-2 m-2 rounded-sm" id="submitForm" @click="this.AddStudent">Додати</button>
                <button class="w-20 cursor-pointer bg-gray-400 text-white p-2 m-2 rounded-sm" id="closeForm" @click="$emit('toggleFormAndList')">Повернутись</button>
            </div>
        </div>
    </div>
</template>
  
<script>
  export default {
    name: 'Form',
    data() {
      return {
        first_name:'',
        last_name:''
      }
    },
    methods: {
      AddStudent(){
        try {
          this.$emit('post-data', {"first_name":this.first_name,"last_name":this.last_name});
        } catch (error) {
          alert("error: "+error);
        }
      }
    },
  }
</script>
  
  