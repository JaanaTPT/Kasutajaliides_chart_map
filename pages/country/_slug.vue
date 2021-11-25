<template>

<div>
 <div>
     <v-row>
        <v-col
            cols="6"
            sm="4"
            md="2"
        >
        <div>
            <v-menu
            v-model="showPicker"
            :close-on-content-click="true"
            transition="scale-transition"
            offset-y
            full-width
            max-width="290px"
            min-width="290px"
            >
            <template v-slot:activator="{ on }">
                <v-text-field
                    v-model="startDate"
                    label="Choose chart start date"
                    persistent-hint
                    readonly
                    v-on="on"
                ></v-text-field>
            </template>
            <v-date-picker
                v-model="startDate"
                no-title
                @input="showPicker = false"
            ></v-date-picker>
            </v-menu>
        </div>
        </v-col>

        <v-col
            cols="6"
            sm="4"
            md="2"
        >
        <div>
            <v-menu
            v-model="showPicker"
            :close-on-content-click="true"
            transition="scale-transition"
            offset-y
            full-width
            max-width="290px"
            min-width="290px"
            >
            <template v-slot:activator="{ on }">
                <v-text-field
                    v-model="endDate"
                    label="Choose chart end date"
                    persistent-hint
                    readonly
                    v-on="on"
                ></v-text-field>
            </template>
            <v-date-picker
                v-model="endDate"
                no-title
                @input="showPicker = false"
            ></v-date-picker>
            </v-menu>
        </div>
        </v-col>
        <v-col
            cols="6"
            sm="4"
            md="2"
        >
        <div> 
             <v-btn @click="getCountry">Refresh</v-btn>
        </div>
         </v-col>
    </v-row>

   <v-btn @click="dataLabel='confirmed'">Confirmed</v-btn>
   <v-btn @click="dataLabel='deaths'">Deaths</v-btn>
   <chart :data="$store.getters[dataLabel]" :labels="$store.getters.labels" :dataLabel="dataLabel" ></chart>
   </div>
</div>
</template>

<script>

import Chart from '~/components/Chart.vue';
export default {
    components: { Chart },
   
    created(){
            let chartObject = {slug: this.$route.params.slug, startDate: this.startDate, endDate: this.endDate};
            this.$store.dispatch('getCountry', chartObject);
    },
    data(){
        return {
            dataLabel: 'confirmed',
            startDate: '2020-02-01',
            endDate: (new Date(Date.now() - (new Date()).getTimezoneOffset() * 60000)).toISOString().substr(0, 10),
        }
    },
    methods: {
        getCountry() {
            let chartObject = {slug: this.$route.params.slug, startDate: this.startDate, endDate: this.endDate};
            this.$store.dispatch('getCountry', chartObject);
        }
    }
}
</script>

<style>

</style>