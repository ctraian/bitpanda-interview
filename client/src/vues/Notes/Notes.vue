<template lang="pug">
  div.notes
    Search(:title='searchTitle' :handleSearch='handleSearch')
    div.notes__content
      div.notes__content__header(
        :class="{'notes__content__header--emptyList': emptyList}"
      ) Take a note
        button.notes__content__header__addNote(@click='updateNotes(notes[0])') +
      Note(
        v-for='({isDone, title, date}, i) in filteredNotes'
        :isLast='filteredNotes.length === ++i'
        :key='`note-${noteCounter}-${noteCounter + i}`'
        :checked='isDone'
        :noteTitle='title'
        date
      )
    Pagination(v-if='notes.length > 3' :prev='prevNotes' :next='nextNotes')
</template>

<script lang="ts">
import {
  computed,
  defineComponent,
  reactive,
  toRefs,
} from '@vue/composition-api';

import Pagination from '../Pagination/Pagination.vue';
import Search from '../Search/Search.vue';
import Note from './Note/Note.vue';

interface noteI{
  isDone: boolean;
  title: string;
  date: number;
}

interface stateI{
  [key: string]: string | boolean | noteI[] | number;
  title: string;
  noNotes: boolean;
  emptyList: boolean;
  notes: noteI[];
  noteCounter: number;
  paginationThreshold: number;
  pThreshold: number;
  searchTitle: string;
}

export default defineComponent({
  name: 'Notes',
  components: {
    Search,
    Note,
    Pagination,
  },
  setup() {
    const state: stateI = reactive({
      title: '',
      noNotes: false,
      notes: [
        {
          isDone: true,
          title: 'Think real hard about whats for lunch',
          date: new Date().getMinutes(),
        },
        {
          isDone: false,
          title: 'Buy some Pantos and start looking for Lambos',
          date: new Date().getMinutes(),
        },
        {
          isDone: false,
          title: 'Be a bit panda',
          date: new Date().getMinutes(),
        },
      ],
      noteCounter: 0,
      paginationThreshold: 3,

      emptyList: computed(() => state.notes.length === 0),
      pThreshold: computed(() => Math.abs(state.paginationThreshold - 3)),
      searchTitle: computed(() => state.title.toLowerCase()),
      filteredNotes: computed(() => (
        state.notes
          .slice(state.pThreshold, state.paginationThreshold)
          .filter((n) => n.title.toLowerCase().includes(state.searchTitle))
      )),
    });

    const handleSearch = (e: Event) => {
      const target = (<HTMLInputElement>e.target);

      state.title = target.value;
    };

    const updateNotes = (note: noteI) => {
      state.notes.push(note);
      state.noteCounter += 1;
    };

    const nextNotes = () => {
      if (state.notes.slice(state.pThreshold, state.paginationThreshold + 1).length === 4) {
        state.paginationThreshold += 3;
      }
    };

    const prevNotes = () => {
      if (state.paginationThreshold > 3) {
        state.paginationThreshold -= 3;
      }
    };

    return {
      ...toRefs(state),
      handleSearch,
      updateNotes,
      nextNotes,
      prevNotes,
    };
  },
});
</script>

<style lang="sass">
@import 'style';
</style>
