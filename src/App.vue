<template>
  <div class="app">
    <div :class="[{ flexStart: step === 1}, 'wrapper']">
        <transition name="slide">
        <img v-if="step === 1" class="logo"  src="../assets/pobrane.svg" alt="">
        </transition>
        <Claim v-if="step === 0"  />
        <Searchinput v-model="searchValue" 
        @input="handleInput" 
        :dark="step === 1"/>
        <transition name="fade">
        <Heroimage v-if="step === 0" />
        </transition>


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
            loading: false,
            step: 0,
            searchValue: '',
            results: [],
        };
    },

    methods: {
        handleInput: debounce (function() {
            this.loading = true;
            axios.get(`${API}?q=${this.searchValue}&media_type=image`)
            .then((response) => {
                this.results = response.data.collection.items;
                this.loading = false;
                this.step = 1;
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

  .fade-enter-active, .fade-leave-active{
      transition: opacity .3s ease;
  }

  .fade-enter, .fade-leave-to{
      opacity: 0;
  }

  
  .slide-enter-active, .slide-leave-active{
      transition: margin-top .3s ease;
  }

  .slide-enter, .slide-leave-to{
      margin-top: -50px;
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
        position: relative;

        &.flexStart{
            justify-content: flex-start;
        }

        .logo{
    position: absolute;
    top: 30px;
}
    }




</style>
