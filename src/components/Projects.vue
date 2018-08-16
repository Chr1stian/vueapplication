<template>
<v-layout>
   <v-flex xs12 sm6 offset-sm3>
     <v-card>
       <v-card-title primary-title>
         <div>
           <h3 class="headline mb-0">Project 1</h3>
         </div>
       </v-card-title>

       <v-card-actions>
         <v-btn flat color="orange">Share</v-btn>
         <v-btn flat color="orange">Explore</v-btn>
       </v-card-actions>
     </v-card>
     <v-card>
       <v-card-title primary-title>
         <div>
           <h3 class="headline mb-0">Project 2</h3>
         </div>
       </v-card-title>

       <v-card-actions>
         <v-btn flat color="orange">Share</v-btn>
         <v-btn flat color="orange">Explore</v-btn>
       </v-card-actions>
     </v-card>
   </v-flex>
 </v-layout>
</template>

<script>
export default {
  name: 'Projects',
  props: {
    msg: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
.project-page-div {
  display: flex;
  flex: center;
}
</style>
