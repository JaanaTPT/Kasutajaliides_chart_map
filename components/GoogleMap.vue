<template>
  <div ref="map"></div>
</template>

<script>
import { Loader } from "@googlemaps/js-api-loader"
export default {
    props: ['center', 'zoom', 'position'],
    mounted(){
        const loader = new Loader({
            apiKey: this.$config.googleApiKey,
            version: "weekly"
        });
        loader.load().then(() => {
            this.map = new google.maps.Map(this.$refs['map'], {
                center: this.center,
                zoom: this.zoom,
            });
            // this.marker = new google.maps.Marker({
            //     position:  this.position,
            //     map: this.map,
            // });
            console.log(this.position)
        });
    },
    data(){
        return {
            map: null
        }
    },
    watch: {
        center(newCenter){
            this.map.panTo(newCenter);
        },
        zoom(newZoom){
            this.map.setZoom(newZoom);
        },
        position(newPosition){
             this.marker = new google.maps.Marker({
                position:  newPosition,
                map: this.map,
            });
        }
    }
}
</script>

<style scoped>
    div {
        height: 800px;
    }
</style>