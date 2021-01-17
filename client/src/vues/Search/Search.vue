<template lang="pug">
  form.search(@submit.prevent)
    button.search__icon
      font-awesome-icon(:icon="faSearch")
    input.search__input(
      type='search'
      placeholder='Search'
      :value='title'
      @input='handleSearch'
    )
</template>

<script lang="ts">
import { faSearch } from '@fortawesome/free-solid-svg-icons';
import { FontAwesomeIcon } from '@fortawesome/vue-fontawesome';
import { defineComponent } from '@vue/composition-api';

export default defineComponent({
  name: 'Search',
  components: {
    FontAwesomeIcon,
  },
  props: {
    title: {
      type: String,
      required: true,
    },
    handleSearch: {
      type: Function,
    },
  },
  setup() {
    return {
      faSearch,
    };
  },
});
</script>

<style lang="sass" scoped>
@import 'style';
</style>
