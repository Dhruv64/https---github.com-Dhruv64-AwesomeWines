<template>
<v-app>
<div>
<div class="display-3 ma-8" align="center">Store
<div v-if="loading" class="loader ma-16" ></div></div>


<!-- <h3 :key="info.id">{{info.}}</h3> -->



<v-container>

    <v-row>
        <v-col sm="10" offset-sm="1" lg="8" offset-lg="2">
            <v-row>
                <v-col 
                v-for="wine in wines.slice(0,20)"
                :key="wine.id"
                xs="12" sm="4" lg="3">
                   <v-card outlined>
                       <v-img :src="wine.image" height="300px" contain class="my-3"></v-img>

                        <v-card-title>
                            <!-- <span class="font-weight-light" grey--text>Name: </span> -->
                            <span class="font-weight text-capitalize" >{{wine.wine}}</span>
                        </v-card-title>
                        <v-card-subtitle>
                            avg rating : {{wine.rating.average}}<br/>
                            <span class="success--text">{{wine.rating.reviews}}</span>

                        </v-card-subtitle>

                   </v-card> 
                </v-col>
            </v-row>
        </v-col>
    </v-row> 

</v-container>


</div>
</v-app>
</template>

<script>
import axios from 'axios'

export default{
    data() {
        return {
            wines: [],
            loading : false
        }
    },
    
    name: 'store-vue',
    
    async mounted() {
        this.loading=true;
        try{
        let result = await axios.get('https://api.sampleapis.com/wines/reds');
        console.log("api data", result.data)
        this.wines = result.data
        this.loading=false;
        }
        catch(error){
            console.log(error)
            this.loading = false
        }
        },
        
    }
</script>

<style lang="scss" scoped>
.loader {
    align-items: center;
  border: 16px solid #f3f3f3;
  border-top: 16px solid #3498db;
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
