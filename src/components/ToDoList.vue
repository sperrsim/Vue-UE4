<template>
  <ul>
    <li v-for="(item, index) in toDoList" :key="index">
    <input type="checkbox" :id="item.name" :value="item.name" v-model="checkeditems">
      {{item.name}}
    </li>
  </ul>
  {{checkeditems}}
</template>

<script>
  import {ref} from 'vue'

  export default {
    props: {
      toDoList: {
        type: Array,
        required: true
      }
    },

    setup(){
      const checkeditems = ref([]);

      return{checkeditems};
    },
  }
</script>

<sytel scoped>
ul {
  list-style: none;
}
</style>