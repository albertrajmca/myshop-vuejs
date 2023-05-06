<template>
    <div>
        <ul>
            <li style="display:block; color:blue; padding:3px;  border:2px" v-for="item in items" :key="item.id">
                {{ item.name }} || 
                {{ item.description }} ||
                {{ item.price }}
            </li>
        </ul>
    </div>
  </template>
  
  <script>
  import axios from 'axios';
  
  export default {
    data() {
      return {
        items: [],
      }
    },
    mounted() {
     axios.get("http://localhost:8000/api/products/list")
      .then((response) => {
        this.items = response.data.data;
      })
      .catch((error) => {
        console.log(error);
      });
  }
  }
  </script>
