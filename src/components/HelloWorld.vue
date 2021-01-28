<template>
<v-app>
     <v-dialog   max-width="500px" v-model="ipDialog">
     <v-card min-height="200px">
       <v-card-title>Intialize</v-card-title>

       <v-card-action>
         <v-container>
          <v-text-field prefix="IP Address:" outlined v-model="ipAddress">   </v-text-field>

          <v-row justify="center">
                     <v-btn @click="ipDialog=!ipDialog" class="green" >
            Done
          </v-btn>
          </v-row>
          </v-container>
          
 
       </v-card-action>
      

    
     </v-card>
   </v-dialog>

    <v-app-bar
      app
      color="primary"
      dark
    >
     
  
      <v-btn
        @click="ipDialog=!ipDialog"
      
      >
        <span class="mr-2">Six Axis Robot</span>
        <v-icon>mdi-key</v-icon>
      </v-btn>
    </v-app-bar>
 <div class="hello">
    <v-container>
    <v-row>
        <v-col lg="3" md="4" cols="6" sm="4" >
        <v-container>
        <v-row align="center"  >
      <v-btn fab @click="jointminus(1)" ><v-icon x-large>mdi-minus</v-icon></v-btn>  <b><h1 style="margin:10px">Joint 1</h1></b> <v-btn @click="jointplus(1)"  fab><v-icon x-large>mdi-plus</v-icon></v-btn>
        </v-row>
        </v-container>
      </v-col>   <v-col lg="3" md="4" cols="6" sm="4" >
        <v-container>
        <v-row align="center"  >
      <v-btn fab @click="jointminus(2)"><v-icon x-large>mdi-minus</v-icon></v-btn>  <b><h1 style="margin:10px">Joint 2</h1></b> <v-btn @click="jointplus(2)" fab><v-icon x-large>mdi-plus</v-icon></v-btn>
        </v-row>
        </v-container>
      </v-col>   <v-col lg="3" md="4" cols="6" sm="4" >
        <v-container>
        <v-row align="center"  >
      <v-btn fab @click="jointminus(3)" ><v-icon x-large>mdi-minus</v-icon></v-btn>  <b><h1 style="margin:10px">Joint 3</h1></b> <v-btn  @click="jointplus(3)" fab><v-icon x-large>mdi-plus</v-icon></v-btn>
        </v-row>
        </v-container>
      </v-col>   <v-col lg="3" md="4" cols="6" sm="4" >
        <v-container>
        <v-row align="center"  >
      <v-btn fab @click="jointminus(4)"><v-icon x-large>mdi-minus</v-icon></v-btn>  <b><h1 style="margin:10px">Joint 4</h1></b> <v-btn @click="jointplus(4)" fab><v-icon x-large>mdi-plus</v-icon></v-btn>
        </v-row>
        </v-container>
      </v-col>   <v-col lg="3" md="4" cols="6" sm="4" >
        <v-container>
        <v-row align="center"  >
      <v-btn fab @click="jointminus(5)"><v-icon x-large>mdi-minus</v-icon></v-btn>  <b><h1 style="margin:10px">Joint 5</h1></b> <v-btn @click="jointplus(5)" fab><v-icon x-large>mdi-plus</v-icon></v-btn>
        </v-row>
        </v-container>
      </v-col>
         <v-col lg="3" md="4" cols="6" sm="4" >
        <v-container>
        <v-row align="center"  >
      <v-btn fab @click="jointminus(6)"><v-icon x-large>mdi-minus</v-icon></v-btn>  <b><h1 style="margin:10px">Joint 6 </h1></b> <v-btn @click="jointplus(6)" fab><v-icon x-large>mdi-plus</v-icon></v-btn>
        </v-row>
        </v-container>
      </v-col>
    </v-row>
    <v-row justify="center">
      <v-btn x-large color="red" @click="auto(1)"><b style="  color:white">Auto</b>
      </v-btn>
    </v-row>
    </v-container>
  </div>  

  </v-app>
 
</template>

<script>
import axios from 'axios'
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  } ,data: () => ({
    ipAddress:"",
    ipDialog:false,
    //
  }),methods:
  {
    jointplus(motorNumber){
   axios({
              method: "GET",
              url:
                "http://"+this.ipAddress+"/jointForward?q="+motorNumber,
              headers: { "Content-Type": "application/json" },
              data: {
                q: motorNumber,
              },
            })
              .then((response) => {
                console.log("success");
             
              })
              .catch((error) => {
                this.successDialog = true;
              }); 
    },
        jointminus(motorNumber){
   axios({
              method: "GET",
              url:
                "http://"+this.ipAddress+"/jointBackward?q="+motorNumber,
              headers: { "Content-Type": "application/json" },
              data: {
                q: motorNumber,
              },
            })
              .then((response) => {
                console.log("success");
             
              })
              .catch((error) => {
                this.successDialog = true;
              }); 
    },
        auto(motorNumber){
   axios({
              method: "GET",
              url:
                "http://"+this.ipAddress+"/auto?q="+motorNumber,
              headers: { "Content-Type": "application/json" },
              data: {
                q: motorNumber,
              },
            })
              .then((response) => {
                console.log("success");
             
              })
              .catch((error) => {
                this.successDialog = true;
              }); 
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
