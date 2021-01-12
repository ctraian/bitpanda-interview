<template lang="pug">
    div
      button.prev(@click='prevPage') <
      span |
      button.next(@click='nextPage') >
</template>

<script lang="ts">
import Vue from 'vue';

export default Vue.extend({
  name: 'Note',
  props: {
    prev: {
      type: undefined,
      required: true,
    },
    next: {
      type: undefined,
      required: true,
    },
  },
  data() {
    return {
      prevPage: this.prev,
      nextPage: this.next,
    };
  },
});
</script>

<style lang="sass" scoped>
@import 'style';
</style>
