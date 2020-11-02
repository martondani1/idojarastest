<template>
    <div>
        <v-row>
            <v-col col="2" md="2">
            </v-col>
            <v-col col="8" md="8" align="center">
                <v-card
                class="mx-auto"
                max-width="400"
                >
                    <div class="my-2 del-btn">
                        <v-btn color="error" fab small depressed>
                        <v-icon class="del">mdi-plus</v-icon>
                        </v-btn>
                    </div>
                    <v-list-item two-line>
                    <v-list-item-content>
                        <v-list-item-title class="headline">
                            <Search weather.name/>
                        </v-list-item-title>
                        <v-list-item-subtitle>Mon, 12:30 PM, Mostly sunny</v-list-item-subtitle>
                    </v-list-item-content>
                    </v-list-item>

                    <v-card-text>
                    <v-row align="center">
                        <v-col class="display-3" cols="6">
                        {{Math.round(weather.main.temp)}}&deg;C
                        </v-col>
                        <v-col cols="6">
                        <v-img
                            src="https://cdn.vuetifyjs.com/images/cards/sun.png"
                            alt="Sunny image"
                            width="92"
                        ></v-img>
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