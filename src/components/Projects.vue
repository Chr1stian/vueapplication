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
         <v-list-tile :key="item.title" @click="">
           <v-list-tile-action>
             <img class="pageurlimg linkimg" src="@/assets/icons-link.png" alt>
           </v-list-tile-action>
           <v-list-tile-content>
             <v-list-tile-title>{{ item.location }}</v-list-tile-title>
           </v-list-tile-content>
         </v-list-tile>
         <v-list-tile :key="item.title" @click="">
           <v-list-tile-action>
             <img class="githubimg linkimg" src="@/assets/GitHub-Mark-120px-plus.png" alt>
           </v-list-tile-action>
           <v-list-tile-content>
             <v-list-tile-title>{{ item.sourcecode }}</v-list-tile-title>
           </v-list-tile-content>
         </v-list-tile>

          <v-card-title class="title">Technologies:</v-card-title>
         <v-list-tile
            v-for="subItem in item.items"
            :key="subItem.title"
            @click=""
          >
          <v-list-tile-action>
            <v-icon></v-icon>
             <img class="linkimg" :src="subItem.icon" alt="tech-icon-image">
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
        {name: 'Project 1', type: 'Hobby/Volunteer project', location: 'Page link', sourcecode: 'Github', info:'Additional information', items: [{title: 'Angular', icon: require('../assets/angular-icon.png')}, {title: 'Node.js', icon: 'nodejsico'}]},
        {name: 'Project 2', type: 'School project'}
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
  width: 45%;
  min-width: 500px;
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
}

.dropdown-header {
  background-color: #EEEEEE;
}
</style>
