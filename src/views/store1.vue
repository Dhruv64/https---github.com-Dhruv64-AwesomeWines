<template>
<div>
    <div class="display-3 ma-8" align="center">Store
      <div>
        <v-card
          flat
          class="py-3"
          >
    <v-card-text>
      <v-row
        align="center"
        justify="center"
      >
        <v-col >
          
        <v-btn-toggle
        mandatory>
        <v-btn v-for="winetype in winetypes" :key="winetype" 
        @click="changelink(winetype)"
        >
        {{winetype}}</v-btn>
        
        </v-btn-toggle> 
        
    </v-col>
    </v-row>
    </v-card-text>
  </v-card> 
    
        <!-- <h3>{{url}}</h3> -->
        <div v-if="loading" class="loader ma-16" ></div>
</div>
</div>

  <div>
      <v-container >
        <v-row class="ma-8">
          <v-col sm="12" md="12">
            <v-row>
              <v-col v-for="wine in wines.slice(0, this.visible)" :key="wine.id" sm="6" md="3">
                <v-card class="pa-8 card" outlined> 
                  <v-img :src="wine.image" contain height="250px" class="card-image"> </v-img>
                  <div class="card-footer">
                  <v-card-title class="card-title">{{ wine.id }} - {{ wine.wine }}</v-card-title>
                   <v-card-text class="card-text">Location :  {{wine.location}} </v-card-text>
                  <v-card-subtitle class="card-text">Rating: {{ wine.rating.average }}<br/>
                  <span class="success--text" >{{wine.rating.reviews}}</span>
                  </v-card-subtitle></div>
                </v-card>
              </v-col>
              </v-row>
          </v-col>
        </v-row>
      </v-container>
    </div>
    <div class="text-center"> 
    <v-btn
      class="ma-8"
      outlined
      color="success"
      large
      @click="viewmore"
    >
     View more...
    </v-btn> 
    </div>



    <v-content>
      <router-view></router-view>
    </v-content>
    </div>

</template>

<script>
import axios from 'axios'

export default{
    data() {
        return {
            wines: [],
            loading : false,
            visible: 20,
            selection: 0,
            link : null,
            url: 'https://api.sampleapis.com/wines/reds',
            winetypes: [
              "reds","whites", "sparkling", "rose" , "desert", "port"
            ]
            
        }
    },
    
    name: 'store-vue',
    
    async mounted() {       //lifecycle hook to the api to extract data
        this.loading=true;
        try{
        let result = await axios.get(this.url);
        console.log("api data", result.data)
        this.wines = result.data
        this.loading=false;
        }
        catch(error){
            console.log(error)
            this.loading = false
        }
        },
    

    methods: {
      async mounted() {       //lifecycle hook to the api to extract data
        this.loading=true;
        try{
        let result = await axios.get(this.url);
        console.log("api data", result.data)
        this.wines = result.data
        this.loading=false;
        }
        catch(error){
            console.log(error)
            this.loading = false
        }
        },
      
      
        viewmore() {        //when view more button is pressed
            this.visible= this.visible + 20
        },

        changelink(path){
          
          this.url = 'https://api.sampleapis.com/wines/' + path
          this.mounted()
          
        }
        


        
       
    }
    
        
    }
</script>

<style lang="scss" scoped>
.loader {
  //align-wines: center;
  border: 16px solid #f3f3f3;
  border-top: 16px solid #4BB543;
  border-radius: 50%;
  width: 100px;
  height: 100px;
  animation: spin 2s linear infinite;
}

@keyframes spin {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(360deg);
  }
}
</style>
