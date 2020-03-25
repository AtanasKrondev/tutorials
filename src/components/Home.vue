<template>
  <app-content>
    <template v-slot:nav>
      <ul>
        <li
          v-for="(s,index) of subjects"
          :key="index"
          :class="{active: index === selectedSubjectIndex}"
          @click="selectSubjectHandler(index)"
        >
          <a>{{s.name}}</a>
        </li>
      </ul>
    </template>
    <template v-slot:info>{{subject.content}}</template>
  </app-content>
</template>

<script>
import AppContent from "./shared/Content";
export default {
  components: {
    AppContent
  },
  props: {
    subjects: {
      type: Array,
      required: true
    }
  },
  data() {
    return {
      selectedSubjectIndex: 0
    };
  },
  methods: {
    selectSubjectHandler(index) {
      this.selectedSubjectIndex = index;
    }
  },
  computed: {
    subject() {
      return this.subjects[this.selectedSubjectIndex];
    }
  }
};
</script>

<style scoped>
</style>