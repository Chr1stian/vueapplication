<template>
  <v-layout>
   <v-flex class="card-flex-container">
     <v-card flat class="card" v-for="(item, index) in projectItems" name="cards">
       <v-navigation-drawer class="drawer" stateless floating permanent>
           <v-toolbar flat class="toolbar">
               <v-toolbar-title>{{item.name}}</v-toolbar-title>
               <v-spacer></v-spacer>
             </v-toolbar>
        <v-divider></v-divider>

       <v-list dense>
         <v-list-tile>
           <v-list-tile-action>
            Type:
           </v-list-tile-action>
           <v-list-tile-content>
             <v-list-tile-title>{{ item.type }}</v-list-tile-title>
           </v-list-tile-content>
         </v-list-tile>
         <v-divider></v-divider>
         <a :href="item.pagelink" arial-label="Link to project page">
         <v-list-tile :key="item.title" @click="" v-if=item.pagelink>
           <v-list-tile-action>
             <img class="pageurlimg linkimg" src="@/assets/icons-link.png" alt>
           </v-list-tile-action>
           <v-list-tile-content>
             <v-list-tile-title>{{ item.location }}</v-list-tile-title>
           </v-list-tile-content>
         </v-list-tile>
       </a>
         <a :href="item.githublink" arial-label="Link to project Github page">
         <v-list-tile :key="item.title" @click="" v-if=item.githublink>
           <v-list-tile-action>
             <img class="githubimg linkimg" src="@/assets/GitHub-Mark-120px-plus.png" alt>
           </v-list-tile-action>
           <v-list-tile-content>
             <v-list-tile-title>Github</v-list-tile-title>
           </v-list-tile-content>
         </v-list-tile>
       </a>

          <v-card-title class="title">Technologies:</v-card-title>
         <v-list-tile
            v-for="subItem in item.items"
            :key="subItem.title"
            @click=""
          >
          <v-list-tile-action class="tech-icon-div">
            <v-icon></v-icon>
             <img class="linkimg" :src="subItem.icon" alt>
          </v-list-tile-action>
            <v-list-tile-content>
              <v-list-tile-title>{{ subItem.title }}</v-list-tile-title>
            </v-list-tile-content>
          </v-list-tile>
       </v-list>

       <v-divider></v-divider>
       <v-card-actions class="dropdown-header">
         Detailed project description

         <v-spacer></v-spacer>
         <v-btn icon @click="showInfo(index)">
           <v-icon>{{ show ? 'keyboard_arrow_down' : 'keyboard_arrow_up' }}</v-icon>
         </v-btn>
       </v-card-actions>
         <v-slide-y-transition class="more-info-container">
           <v-card-text v-if="currentlyShowing === index">
             {{item.info}}
           </v-card-text>
          </v-slide-y-transition>
      </v-navigation-drawer>
     </v-card>
   </v-flex>
 </v-layout>
</template>

<script>
export default {
  name: 'Projects',
  props: {
    msg: String
  },
  data() {
    return {
      projectItems: [
        {name: 'Automatic Kiosk Accounting', type: 'Hobby/Volunteer Project', pagelink: null, githublink: 'https://github.com/dotkom/onlineweb4', location: '', info:'Currently in the planning phase. An effort to make the existing kiosk system for the students be automatically accounted trough our accountsystems (fiken) API', items: [{title: 'Django', icon: require('../assets/django-icon.png')}, {title: '(HAL)REST API', icon: ''}]},
        {name: 'Project Page (current)', type: 'Hobby Project', pagelink: null, githublink: 'https://github.com/Chr1stian/vueapplication', location: '', info:'Small personal project to test out new technologies and give an overwiew of some of my project. Setup with docker image and one line push/deploy to dokku server on DigitalOcean', items: [{title: 'Vue', icon: require('../assets/vue-icon.png')}, {title: 'Docker', icon: require('../assets/docker-icon.png')}]},
        {name: 'Car Usage Mobile Application', type: 'Bachelor Project', pagelink: null, githublink: 'https://github.com/TK-data/BilparkApp', location: '', info:'Customers for the project were Trondheim Kommune and Sparebank 1 Bilplan. Fullstack mobile application for both iOS and Android made with React Native. The application lets a user track their car usage and cost, connected with license number through Statens Vegvesens (closed) API.', items: [{title: 'React Native', icon: require('../assets/reactnative-icon.png')}, {title: 'Sails.js', icon: require('../assets/sails-icon.png')}, {title: 'MySQL', icon: require('../assets/mysql-icon.png')}]},
        {name: 'Winesearch Web Application', type: 'School Project', pagelink: 'http://178.62.89.152:8082/', githublink: 'https://github.com/Chr1stian/it2810-webutvikling-h17-prosjekt-4-group-37', location: 'Page link', info:'NB: Some items might be bugged because the database is outdated. First project using Angular, developed as part of a course in three weeks. Uses the "MEAN-stack" which is full and amongst other lets the user save favorite wines and stores last searches', items: [{title: 'Angular', icon: require('../assets/angular-icon.png')}, {title: 'Node.js', icon: require('../assets/node-icon.png')}, {title: 'MongoDB', icon: require('../assets/mongodb-icon.png')}]},
        {name: 'Personal Planner Web Application', type: 'School Project', pagelink: 'http://178.62.89.152:8080/', githublink: 'https://github.com/Chr1stian/it2810-webutvikling-h17-prosjekt-3-group-37', location: 'Page link', info:'First React project developed as part of a course in two weeks. Uses localstorage to remember user entries and displays collected information on a smart homepage', items: [{title: 'React', icon: require('../assets/react-icon.png')}, {title: 'Node.js', icon: require('../assets/node-icon.png')}]},
        {name: 'Coursehelp Mobile Application', type: 'School Project', pagelink: null, githublink: 'https://github.com/prodoteam', location: '', info:'Android application developed to let students follow a course with questions and feedback realtime. Java application to let professors enter course info and answer students questions/see feedback.', items: [{title: 'Android', icon: require('../assets/android-icon.png')}, {title: 'Java', icon: require('../assets/java-icon.png')}, {title: 'MySQL', icon: require('../assets/mysql-icon.png')}]},
        {name: 'Raspberry PI', type: 'Hobby projects', pagelink: null, githublink: null, location: '', info:'Home projects on the Raspberry PI also utilizing Arduino cards and electronic components. Network crawling with python to send welcome message on "facebook messenger" to guests upon arrival. MySQL database hosted for other projects and also setup to be used as web-server.', items: [{title: 'Python', icon: require('../assets/python-icon.png')}, {title: 'MySQL', icon: require('../assets/mysql-icon.png')}]},
        ],
      show: false,
      currentlyShowing: null
    }
  },
  methods:{
    showInfo: function (index) {
      if(this.currentlyShowing === index){
        this.currentlyShowing = null;
      } else {
        this.currentlyShowing = index;
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.card-flex-container {
  display: flex;
  align-items: center;
  flex-wrap: wrap;
  flex-direction: row;
  background-color: #BDBDBD;
}

.drawer {
  width: 100% !important;
}

.card {
  margin: 20px;
  flex-direction: row;
  width: 30%;
  min-width: 350px;
  min-height: 350px;
  flex: 1;
}
.more-info-container {
  height: 75%;
}
.linkimg {
  width: 30px;
}

.toolbar {
  background-color: #EEEEEE;
}

.title {
  background-color: #EEEEEE;
  font-size: 90% !important;
}

.tech-icon-div {
  margin-right: 10px;
}

.dropdown-header {
  background-color: #EEEEEE;
}
</style>
