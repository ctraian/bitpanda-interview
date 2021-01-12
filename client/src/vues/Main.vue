<template lang="pug">
    main
      Notes
</template>

<script lang="ts">
import Vue from 'vue';

import Notes from './Notes/Notes.vue';

export default Vue.extend({
  name: 'Main',
  components: {
    Notes,
  },
});
</script>
