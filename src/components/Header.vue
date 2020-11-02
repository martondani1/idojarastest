<template>
    <header class="header">
        <h1>Weather app</h1>
        <div id="nav">
            <v-chip class="ma-2">
                <router-link to="/">Home</router-link>
            </v-chip>
            <v-chip class="ma-2">
                <router-link to="/about">About</router-link>
            </v-chip>
            
        </div>
    </header>
</template>

<script>

export default {
    name: "Header"
}
</script>

<style scoped>
    .header{
        background: #00bcd4;
        color: #fff;
        text-align: center;
        padding: 30px;
    }
    .header a{
        color: rgb(0, 0, 0);
        padding: 10px;
        text-decoration: none;
    }
</style>