<template lang="pug">
  #app.todo-app
    Main
</template>

<script lang="ts">
import { defineComponent } from '@vue/composition-api';

import Main from './vues/Main.vue';

export default defineComponent({
  name: 'App',
  components: {
    Main,
  },
  setup() {
    // utilise todo-bitpanda-server to get data

    return {
      message: 'Todo list should be here',
    };
  },
});
</script>

<style lang="scss">
html{
  background: #E5E5E5;
}
.todo-app {
  background: #E5E5E5;
  text-align: center;
}
</style>
