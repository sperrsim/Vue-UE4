<template>
  <ul>
    <li v-for="(item, index) in toDoList" :key="index">
    <input
        type="checkbox"
        :id="item.name"
        :value="item.name"
        v-model="checkedItems"
      />
      <span :class="{finished: taskDone(item.name)}"> {{ item.name }}</span>

      <span class="delete" @click="deleteItem(index)">X</span>
    </li>
  </ul>
</template>

<script>
  import { ref } from 'vue';
  export default {  
  props: {
    deleteItem: {
      type: Function,
      required: true,
    },
    toDoList: {
      type: Array,
      require: true,
    },
  },
  setup() {
    const checkedItems = ref([]);

    function taskDone(task) {
      console.log('task: ' + task);
      if (checkedItems.value.includes(task)) 
      {
        return true;
      }
      return false;
    }

    return { checkedItems,
              taskDone };
    
  },
  };
</script>

<style scoped>
ul {
  list-style: none;
}

.finished {
  text-decoration: line-through;
}
</style>