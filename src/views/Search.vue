<template>
    <div class="wrapper">
        <div class="search">
            <input @input="handleInput" id="search" name="search" v-model="searchValue" placeholder="search">
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
const API = 'https://images-api.nasa.gov/search';
export default {
    name: 'Search',
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
        padding: 30px;
        margin: 0;
        display: flex;
        flex-direction: column;
        align-items:center;
    }

    .search{
        width: 250px;
        display: flex;
        flex-direction: column;
        font-family: Montserrat, sans-serif;

        input{
            height: 30px;
            border: 0;
            border-bottom: 1px solid black;

        }
    }


</style>
