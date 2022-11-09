<template>
  <form @submit.prevent="doCreate">
    <input v-model="item" placeholder="Enter ToDO" />
    <button>Create</button>
  </form>
</template>

<script>
import { ref } from 'vue';

export default {
  props: {
    create: { Function, required: true },
  },

  setup(props) {
    let item = ref('');

    function doCreate() {
      console.log('Create ...' + item.value);
      props.create(item.value);
      item.value='';
    }

    return { item, doCreate };
  },
};
</script>

<style scoped></style>
