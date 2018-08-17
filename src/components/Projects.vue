<template>
  <v-layout>
   <v-flex class="card-flex-container">
     <v-card class="card" v-for="item in projectItems" name="cards">
       <v-card-title primary-title>
         <div>
           <h3 class="headline mb-0">{{item.name}}</h3>
         </div>
       </v-card-title>


       <v-card-text>{{item.type}}</v-card-text>

       <v-card-actions>
         <v-btn flat color="orange">Github</v-btn>
         <v-btn flat color="orange">Page</v-btn>
         <v-spacer></v-spacer>
         <v-btn icon @click="show = !show">
           <v-icon>{{ show ? 'keyboard_arrow_down' : 'keyboard_arrow_up' }}</v-icon>
         </v-btn>
       </v-card-actions>


       <v-slide-y-transition class="more-info-container">
         <v-card-text v-show="show">
           HALLABALLA!
         </v-card-text>
        </v-slide-y-transition>

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
        {name: 'Project 1', type: 'Hobby/Volunteer project'},
        {name: 'Project 2', type: 'School project'}
      ],
      show: 'false'
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
}
.card-flex-container {
  display: flex;
  align-items: center;
  flex-wrap: wrap;
  flex-direction: row;
  background-color: #3c3e42;
}
.card {
  margin: 20px;
  padding: 10px;
  flex-direction: row;
  background-color: #61646b;
  width: 45%;
  flex: 1;
}
.more-info-container {
  height: 75%;
}
</style>
