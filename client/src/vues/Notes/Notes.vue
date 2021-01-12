<template lang="pug">
    div
      Search(search)
      div.container
        div.header(:class='{emptyList: noNotes}') {{inputText}}
          button(@click='updateNotes(notes[0])') +
        Note(
          v-for='({isDone, title, date}, i) in notes.slice(pThreshold, paginationThreshold)'
          :isLast='i !== 0 && i % 2 === 0'
          :key='`note-${noteCounter}-${noteCounter + i}`'
          :checked='isDone'
          :noteTitle='title'
          date
        )
      Pagination(v-if='notes.length > 3' :prev='prevNotes' :next='nextNotes')
</template>

<script lang="ts">
import Vue from 'vue';

import Pagination from '../Pagination/Pagination.vue';
import Search from '../Search/Search.vue';
import Note from './Note/Note.vue';

interface NoteI{
  isDone: boolean;
  title: string;
  date: number;
}

export default Vue.extend({
  name: 'Notes',
  components: {
    Search,
    Note,
    Pagination,
  },
  data() {
    return {
      search: '',
      inputText: 'Take a note',
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
    };
  },
  computed: {
    pThreshold(): number {
      return Math.abs(this.paginationThreshold - 3);
    },
  },
  methods: {
    updateNotes(note: NoteI) {
      this.notes.push(note);
      this.noteCounter += 1;
    },
    nextNotes() {
      if (this.notes.slice(this.pThreshold).length > 3) {
        this.paginationThreshold += this.paginationThreshold;
      }
    },
    prevNotes() {
      if (this.paginationThreshold > 3) {
        this.paginationThreshold -= 3;
      }
    },
  },
});
</script>

<style lang="sass" scoped>
@import 'style';
</style>
