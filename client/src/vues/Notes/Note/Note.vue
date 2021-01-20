<template lang="pug">
  div.note(:class="{'note--lastNote': isLast}")
    input.note__checkbox(
      name='check input'
      :class="{'note__checkbox--isChecked': checked}"
      type='checkbox'
      @click="checked = !checked"
    )
    span.note__title(:class="{'note__title--isChecked': checked}") {{noteTitle}}
    span.note__date - {{ new Date().getMinutes()}} minutes
</template>

<script lang="ts">
import { defineComponent } from '@vue/composition-api';

export default defineComponent({
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
});
</script>

<style lang="sass">
@import 'style';
</style>
