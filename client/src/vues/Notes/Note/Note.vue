<template lang="pug">
    div(:class='{lastNote}')
      input(:class='{isChecked}' type='checkbox' @click="isChecked = !isChecked")
      span(:class='{isChecked}') {{noteTitle}}
      span.date - {{ new Date().getMinutes()}} minutes
</template>

<script lang="ts">
import Vue from 'vue';

export default Vue.extend({
  name: 'Note',
  props: {
    checked: {
      type: Boolean,
      required: true,
    },
    noteTitle: {
      type: String,
      required: true,
    },
    isLast: {
      type: Boolean,
    },
  },
  data() {
    return {
      isChecked: this.checked,
      title: this.noteTitle,
      lastNote: this.isLast,
    };
  },
});
</script>

<style lang="sass" scoped>
@import 'style';
</style>
