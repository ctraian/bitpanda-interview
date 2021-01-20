<template lang="pug">
    main#main
      Notes
</template>

<script lang="ts">
import { defineComponent } from '@vue/composition-api';

import Notes from './Notes/Notes.vue';

export default defineComponent({
  name: 'Main',
  components: {
    Notes,
  },
});
</script>
