<template>
  <div id="app">
    <app-header></app-header>
    <main>
      <app-navigation @navigate="navigationHandler($event)" :nav-items="tutorials.technologies"></app-navigation>
      <!-- <app-home :subjects="subjects"></app-home> -->
      <!-- <app-login></app-login> -->
      <!-- <app-register></app-register> -->
      <!-- <app-create-subject
        :subjects="subjects"
        :technologies="tutorials.technologies"
        @create="createHanlder($event)"
      ></app-create-subject> -->
      <app-register-form></app-register-form>
    </main>
    <app-footer></app-footer>
  </div>
</template>

<script>
import tutorials from "./tutorials.json";

import AppHeader from "./components/core/Header";
import AppFooter from "./components/core/Footer";
import AppNavigation from "./components/core/Navigation";
// import AppHome from "./components/Home";
// import AppLogin from "./components/Login";
// import AppRegister from "./components/Register";
import AppRegisterForm from "./components/RegisterForm";
// import AppCreateSubject from "./components/CreateSubject";

export default {
  name: "App",
  components: {
    AppHeader,
    AppFooter,
    AppNavigation,
    // AppHome,
    // AppLogin,
    // AppRegister,
    // AppCreateSubject
    AppRegisterForm,
  },
  data() {
    return {
      tutorials,
      selectedTechIndex: 0
    };
  },
  methods: {
    navigationHandler(index) {
      this.selectedTechIndex = index;
    },
    createHanlder({ technologyId, subject: name, htmlContent: content }) {
      const selectedTechnology = this.tutorials.technologies.find(
        t => t.id === technologyId
      );
      selectedTechnology.subjects = selectedTechnology.subjects.concat({
        name,
        content
      });
    }
  },
  computed: {
    subjects() {
      return this.tutorials.technologies[this.selectedTechIndex].subjects;
    }
  }
};
</script>

<style>
@import url("https://fonts.googleapis.com/css?family=Lato&display=swap");
body {
  font-family: "Lato", sans-serif;
}

#app {
  font-family: "Lato", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
