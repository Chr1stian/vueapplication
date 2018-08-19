<template>
  <v-app class="app">

    <v-content>
      <Projects/>
    </v-content>

    <v-footer class="footer" :fixed="fixed">
      <span>&copy; 2018</span>
      <div>
        <span><a href="https://www.linkedin.com/in/christiannyvoll/" arial-label="Link to creator LinkedIn profile"><img class="linkedinimg linkimg" src="@/assets/In-2C-128px-TM.png" alt></a></span>
        <span><a href="https://github.com/Chr1stian"  arial-label="Link to creator Github profile"><img class="githubimg linkimg" src="@/assets/GitHub-Mark-120px-plus.png" alt></a></span>
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
  background-color: #BDBDBD;
}
.footer {
  display: flex;
  align-content: space-between;
  justify-content: space-between;
  padding-left: 10px;
  padding-right: 10px;
  height: 65px !important;
}
.linkimg {
  width: 30px;
}


</style>
