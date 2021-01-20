<template lang="pug">
    div.pagination
      button.pagination__btn(class='pagination__btn__prev' @click='prev') <
      span.pagination__separator |
      button.pagination__btn(class='pagination__btn__next' @click='next') >
</template>

<script lang="ts">
import { defineComponent } from '@vue/composition-api';

export default defineComponent({
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
});
</script>

<style lang="sass">
@import 'style';
</style>
