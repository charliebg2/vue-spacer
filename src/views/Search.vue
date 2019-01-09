<template>
    <div class="wrapper">
        <Claim />
        <Searchinput />
            <!-- <input @input="handleInput" id="search" name="search" v-model="searchValue" placeholder="search"> -->
            <!-- <ul>
                <li v-for="item in results" :key="item.data[0].nasa_id">
                    <p>{{item.data[0].description}}</p>
                </li>
            </ul> -->

    </div>
</template>

<script>
import axios from 'axios';
import debounce from 'lodash.debounce';
import Claim from '@/components/Claim.vue';
import Searchinput from '@/components/Searchinput.vue';

const API = 'https://images-api.nasa.gov/search';
export default {
    name: 'Search',
    components: { 
        Claim, 
        Searchinput,
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

<style lang="scss" scoped>

    .wrapper{
        width: 100%;
        padding: 30px ;
        margin: 0;
        display: flex;
        flex-direction: column;
        align-items:center;
        height: 100vh;
        background-repeat: no-repeat;
        background-position: 80% 0%;
        background-size: cover;
        justify-content: center;
        background-image: url('../../assets/heroimage.jpg');
    }


</style>
