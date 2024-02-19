<template>
  <div class="m-10 p-10 shadow-xl rounded-xl bg-white">
    <h1 class="font-bold text-2xl mb-4 underline underline-offset-2">JQuery</h1>
    <!--<button @click="LoadData" class="bg-green-400 text-white p-2 m-2 cursor-pointer rounded-sm" >Click me!</button>-->
    <List @toggle-form-and-list="this.toggleFormAndList" :items="this.data" v-if="listIsActive"/>
    <Form @toggle-form-and-list="this.toggleFormAndList" @post-data="PostData" v-if="formIsActive"/>
    </div>
</template>

<script>
import Form from '../components/Form.vue';
import List from '../components/List.vue';
import axios from 'axios';

export default { 
  mounted() {
    this.LoadData();
  },
  name: 'Card',
  components: {
    Form,
    List
  },
  data() {
    return { 
      formIsActive: false,
      listIsActive:true,
      //items:[{id:0,text:"aaa"},{id:1,text:"bbb"},{id:2,text:"ccc"},{id:3,text:"ddd"}],
      data:null
    }
  },
  methods: {
    toggleFormAndList(){
      this.formIsActive=!this.formIsActive;
      this.listIsActive=!this.listIsActive;
      console.log(this.formIsActive);
      console.log(this.listIsActive);
    },
    LoadData(){
      axios.get('http://localhost:8000/api/students')
      .then(response => {
        this.data = response.data;
        //console.log(response);
      })
      .catch(error => {
        console.error('Error fetching data:', error);
      });
    },
    PostData(data){
      axios.post('http://localhost:8000/api/student', data)
        .then((res) => {
          console.log(res.data)
          this.LoadData();
          this.toggleFormAndList();
        })
        .catch((error) => {
            console.error('Error fetching data:', error);
        });
    }
  },
}
</script>

