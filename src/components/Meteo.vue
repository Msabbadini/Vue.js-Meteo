<template>
    <div class="container">
        <h1 class="my-4"> App météo avec Vue.js</h1>

        <div class="form-groupe mb-5">
            <label for="position">Le nom d'une ville</label>
            <input 
            type="text" 
            id="position"
            class="form-control"
            v-model="requete"
            @keypress.enter='goMeteo'
            >
        </div>
        <div class="w-75 m-auto" v-if='temps'>
            <h3 class="text-center mb-3">Position: {{temps.name}} </h3>
            <div class="card text-center p-5">
                <p class="texte-affichage">
                    temperature: {{temps.main.temp.toFixed()}}
                </p>
            <p class="texte-affichage">
                Temps: {{temps.weather[0].description}}
            </p>
            </div>
        </div>
    </div>      
</template>

<script>
import axios from 'axios'

export default{
    name: 'Meteo',
    data(){
        return{
            requete:'',
            temps:undefined,
            api_code:'35292726acb3039ee92ae9f1bfd91aed',
            url_recherche:'https://api.openweathermap.org/data/2.5/weather?'
        }
    },
    methods: {
        goMeteo(){
                axios
                .get(`${this.url_recherche}q=${this.requete}&units=metric&APPID=${this.api_code}&lang=fr`)
                .then(reponse=>{
                    this.temps = reponse.data;
                })
                this.requete='';
            }
    }
}
</script>

<style>
.texte-affichage{
    font-size: 30px;
    font-weight: 300;
    line-height: 1.2;
}


</style>