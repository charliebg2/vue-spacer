<template>
  <div class="app">
    <div class="wrapper">
        <Claim />
        <Searchinput v-model="searchValue" @input="handleInput"/>
        <Heroimage />
            <!-- <input @input="handleInput" id="search" name="search" v-model="searchValue" placeholder="search"> -->
           <ul>
                <li v-for="item in results" :key="item.data[0].nasa_id">
                    <p>{{item.data[0].description}}</p>
                </li>
            </ul>

    </div>
  </div> 
  
</template>

<script>
import axios from 'axios';
import debounce from 'lodash.debounce';
import Claim from '@/components/Claim.vue';
import Searchinput from '@/components/Searchinput.vue';
import Heroimage from '@/components/Heroimage.vue';

const API = 'https://images-api.nasa.gov/search';
export default {
    name: 'App',
    components: { 
        Claim, 
        Searchinput,
        Heroimage,
        },


    data() {
        return{
            searchValue: '',
            results: [],
        };
    },

    methods: {
        handleInput: debounce (function() {
            axios.get(`${API}?q=${this.searchValue}&media_type=image`)
            .then((response) => {
                this.results = response.data.collection.items;
            })
            .catch((error) => {
                console.log(error);
            });
        }, 500),
    },
};
</script>

<style lang="scss">
@import url('https://fonts.googleapis.com/css?family=Montserrat:400,600,800');

  *{
    box-sizing: border-box;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
  }
    $desktop: 840px;
    $ipad: 768px;
    $smalls: 400px;


@mixin desktop{
    @media (min-width: #{$desktop}){
        @content;
    }
}

@mixin smalls{
    @media (min-width: #{$smalls}){
        @content;
    }
}

@mixin ipad{
    @media (min-width: #{$ipad}){
        @content;
    }
}

  body{
    font-family: 'Montserrat', sans-serif;
    margin: 0;
    padding: 0;
  }

    .wrapper{
        width: 100%;
        color: white;
        padding: 30px ;
        margin: 0;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items:center;
        min-height: 100vh;
    }

</style>
