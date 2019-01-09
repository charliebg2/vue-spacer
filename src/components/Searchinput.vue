<template>
    <div class="searchWrapper">
        <input @input="handleInput" id="search" name="search" v-model="searchValue" placeholder="search"/>
    </div>
</template>

<script>
export default {
    name: 'Searchinput',
}
</script>

<style lang="scss" scoped>

    // .searchWrapper{
    //     width: 100%;
    //     padding: 30px ;
    //     margin: 0;
    //     display: flex;
    //     flex-direction: column;
    //     align-items:center;
    // }

    .searchWrapper{
        width: 250px;
        display: flex;
        flex-direction: column;
        font-family: Montserrat, sans-serif;
        padding: 30px 0;

        input{
            height: 30px;
            border: 0;
            border-bottom: 1px solid black;
            background: none;
            color: black;
        }
    }

</style>
