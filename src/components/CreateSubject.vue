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
    <template v-slot:content>
      <div class="form-group">
        <input placeholder="Technology subject..." type="text" id="subject" v-model="subject" />
      </div>
      <vue-editor v-model="htmlContent"></vue-editor>
      <select name="technologies" id="technologies" v-model="technologyId">
        <option :value="null" selected>Select a technology...</option>
        <option v-for="item in technologies" :key="item.id" :value="item.id">{{item.name}}</option>
      </select>
      <button class="btn" @click="createSubjectHandler()">Create</button>
      <h3>Content preview</h3>
      <div class="content-preview" v-html="htmlContent"></div>
    </template>
  </app-content>
</template>

<script>
import AppContent from "./shared/Content";
import { VueEditor } from "vue2-editor";

export default {
  components: {
    AppContent,
    VueEditor
  },
  props: {
    subjects: {
      type: Array,
      required: true
    },
    technologies: {
      type: Array,
      required: true
    }
  },
  data() {
    return {
      selectedSubjectIndex: 0,
      subject: "",
      htmlContent: "",
      technologyId: null
    };
  },
  methods: {
    selectSubjectHandler(index) {
      this.selectedSubjectIndex = index;
    },
    createSubjectHandler() {
      const { technologyId, subject, htmlContent } = this.$data;
      this.$emit("create", { technologyId, subject, htmlContent });
      this.technologyId = null;
      this.subject = "";
      this.htmlContent = "";
    }
  },
  computed: {
    selectedSubject() {
      return this.subjects[this.selectedSubjectIndex];
    }
  }
};
</script>

<style scoped>
.content-preview {
  text-align: left;
  word-wrap: break-word;
  display: block;
  width: 100%;
}

select {
  -webkit-appearance: none;
  -moz-appearance: none;
  text-indent: 1px;
  text-overflow: "";
}

div.form-group input,
option,
select {
  font-size: 18px;
  padding: 1%;
  width: 25%;
  border: none;
  border-bottom: 1px solid black;
  font-size: 16px;
  font-family: inherit;
  text-align: center;
  text-align-last: center;
}
</style>