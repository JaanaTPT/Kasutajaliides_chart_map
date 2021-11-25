<template>
<div>
  <v-row> 
    <v-col
          cols="12"
          sm="6"
          md="3"
        >
          <v-text-field
            v-model="center.lat"
            label="Select latitude for map center"
            type="number"
          ></v-text-field>
    </v-col>
    <v-col
          cols="12"
          sm="6"
          md="3"
        >
          <v-text-field
            v-model="center.lng"
            label="Select longitude for map center"
            type="number"
          ></v-text-field>
    </v-col>
    <v-col
          cols="12"
          sm="6"
          md="3"
        >
          <v-text-field
            v-model="zoom"
            label="Select zoom"
            type="number"
          ></v-text-field>
    </v-col>
    <v-col
          cols="12"
          sm="6"
          md="3"
        >
        <div> 
             <v-btn @click="center={lat:Number(center.lat), lng:Number(center.lng)}; zoom=Number(zoom)">Change center and zoom</v-btn>
        </div>
    </v-col>
  </v-row>


  <v-row> 
    <v-col
          cols="12"
          sm="6"
          md="3"
        >
          <v-text-field
            v-model="position.lat"
            label="Select latitude for marker position"
            type="number"
          ></v-text-field>
    </v-col>
    <v-col
          cols="12"
          sm="6"
          md="3"
        >
          <v-text-field
            v-model="position.lng"
            label="Select longitude for marker position"
            type="number"
          ></v-text-field>
    </v-col>
    <v-col
          cols="12"
          sm="6"
          md="3"
        >
          <div></div>
    </v-col>
    <v-col
          cols="12"
          sm="6"
          md="3"
        >
        <div> 
             <v-btn @click="position={lat:Number(position.lat), lng:Number(position.lng)}">Add marker</v-btn>
        </div>
    </v-col>
  </v-row>

    <v-btn @click="center={lat: 45, lng:25}; zoom=10">go to somewhere</v-btn>
  <google-map :center="center" :zoom="zoom" :position="position"></google-map>
</div>
</template>

<script>
import GoogleMap from '~/components/GoogleMap.vue'

export default {
  components: { GoogleMap },
  data(){
      return {
          center: {lat: 44, lng: 24},
          zoom: 4,
          position: {lat: 58, lng: 27},
      }
  }
   
}
</script>

<style>
   
</style>