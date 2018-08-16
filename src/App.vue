<template>
  <v-app class="app">

    <v-content>
      <Projects/>
    </v-content>

    <v-footer class="footer" :fixed="fixed">
      <span>&copy; 2018</span>
      <div>
        <span><a href="https://www.linkedin.com/in/christiannyvoll/"><img class="linkedinimg" src="@/assets/In-2C-14px.png" alt=""></a></span>
        <span><a href="https://github.com/Chr1stian"><img class="githubimg" src="@/assets/GitHub-Mark-32px.png" alt=""></a></span>


      </div>
      <span>Christian Nyvoll</span>
    </v-footer>
  </v-app>
</template>

<script>
import Projects from './components/Projects'

export default {
  name: 'App',
  components: {
    Projects
  },
  data () {
    return {
      clipped: false,
      drawer: true,
      fixed: false,
      items: [{
        icon: 'bubble_chart',
        title: 'Inspire'
      }],
      miniVariant: false,
      right: true,
      rightDrawer: false,
      title: 'Vuetify.js'
    }
  }
}
</script>

<style scoped>
.app {
  background-color: #3c3e42;
}
.footer {
  display: flex;
  align-content: space-between;
  justify-content: space-between;
  padding-left: 10px;
  padding-right: 10px;
}
.linkedinimg {
  width: auto;
  height: auto;
}


</style>
