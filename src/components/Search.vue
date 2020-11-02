<template>
    <div>
        <v-row>
            <v-col cols="2" md="2">
            </v-col>
            <v-col cols="8" md="8" align="center">
                    <v-text-field color="cyan" v-model="query" label="Search city"></v-text-field>
                    <v-btn @click="fetchWeather()" color="cyan" depressed>Search...</v-btn>           
            </v-col>
            <v-col cols="2" md="2"></v-col>
        </v-row>
        <v-row v-if="typeof weather.main != 'undefined'">
            <v-col col="2" md="2">
            </v-col>
            <v-col col="8" md="8" align="center">
                <v-card
                class="mx-auto"
                max-width="400"
                >
                <!--<div class="my-2 del-btn">
                        <v-btn color="error" fab small depressed>
                        <v-icon class="del">mdi-plus</v-icon>
                        </v-btn>
                    </div>-->
                    <v-list-item two-line>
                    <v-list-item-content>
                        <v-list-item-title class="headline">{{weather.name}}</v-list-item-title>
                        <v-list-item-subtitle>{{dateBuilder()}}, {{weather.weather[0].main}}</v-list-item-subtitle>
                    </v-list-item-content>
                    </v-list-item>

                    <v-card-text>
                    <v-row align="center">
                        <v-col class="display-3" cols="6">
                        {{Math.round(weather.main.temp)}}&deg;C
                        </v-col>
                        <v-col cols="6">
                        <img id="weather-icon"
                            :src='setIcon()'
                            width="92"
                        >
                        </v-col>
                    </v-row>
                    </v-card-text>
                </v-card>
            
            </v-col>
            <v-col col="2" md="2"></v-col>
        </v-row>
    </div>
</template>


<script>

export default {
    name: 'Search',
    data(){
        return{
            api_key: 'e9731791a12ad5cd61caeffd68009709',
            url_base: 'http://api.openweathermap.org/data/2.5/',
            query: '',
            weather: {},
            weatherIcons: {
                cloud: 'https://cdn4.iconfinder.com/data/icons/weather-129/64/weather-2-512.png',
                rain: 'https://img.icons8.com/all/500/rain.png',
                clear: 'https://cdn.onlinewebfonts.com/svg/img_177473.png'
            }
        }
    },
    methods:{
        fetchWeather() {
            fetch(`${this.url_base}weather?q=${this.query}&units=metric&appid=${this.api_key}`)
                .then(res => {
                    return res.json();
                }).then(this.setResults)
            
        },
        setResults(results){
            this.weather = results;
            
        },
        dateBuilder(){
            let d = new Date();
            let days = ["Sun", "Mon", "Tue", "Wed", "Thu", "Fri", "Sat"];
            let day = days[d.getDay()];
            let hours = d.getHours();
            let minutes = d.getHours();
            return `${day} ${hours}:${minutes}`;
        },
        setIcon(){
            if (this.weather.weather[0].main == 'Rain') {
                return this.weatherIcons.rain
            }
            else if (this.weather.weather[0].main == 'Clouds') {
                return this.weatherIcons.cloud
            }
            else if (this.weather.weather[0].main == 'Clear') {
                return this.weatherIcons.clear
            }
            return 'null'
        }
    }

    
}

</script>

<style scoped>

.del{
    transform: rotate(45deg);
}
.del-btn{
    position: absolute;
    top: 70px;
    right: 15px;
}

</style>