<template lang="pug">
    form(v-on:submit.prevent)
        button
            font-awesome-icon(:icon="searchIcon" @click='search')
        input(type='search' @change='filter' :placeholder='inputText')
</template>

<script lang="ts">
import { faSearch } from '@fortawesome/free-solid-svg-icons';
import { FontAwesomeIcon } from '@fortawesome/vue-fontawesome';
import Vue from 'vue';

export default Vue.extend({
  name: 'Search',
  props: {
    search: {
      type: String,
    },
  },
  data() {
    return {
      inputText: 'Search',
      searchIcon: faSearch,
      title: this.search,
    };
  },
  components: {
    FontAwesomeIcon,
  },
  methods: {
    filter() {
      console.log('I don t know vuejs typescript events');
    },
  },
});
</script>

<style lang="sass" scoped>
@import 'style';
</style>
