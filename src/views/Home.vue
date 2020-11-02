<template>
  <div class="home">
    <Header />
    <v-container>
      <Search />
      <!--<Card />-->
    </v-container>
  </div>
</template>

<script>
// @ is an alias to /src
import Header from '../components/Header'
import Search from '../components/Search'
//import Card from '../components/Card'

export default {
  name: 'Home',
  components: {
    Header,
    Search,
    //Card
  },
  data(){
    return{
      api_key:'e9731791a12ad5cd61caeffd68009709'
    }
  }
}
</script>
