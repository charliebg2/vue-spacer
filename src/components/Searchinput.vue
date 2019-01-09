<template>
    <div class="searchWrapper">
        <input  
        id="search" 
        name="search" 
        @input="handleChange"
        :value="value"
        placeholder="search"/>
    </div>
</template>

<script>
export default {
    name: 'Searchinput',
    props: {
        value: {
            type: String,
            required: true,
        },
    },
    methods: {
        handleChange(e) {
            this.$emit('input', e.target.value);
        },
    },
};

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
        padding: 40px 0;

        input{
            height: 30px;
            border: 0;
            text-align: center;
            font-size: 16px; 
            border-bottom: 1px solid white;
            background: none;
            color: white;
            transition: box-shadow .5s;
        }
        input:focus{
            outline:none;
            box-shadow: 0 6px 20px -8px  white;
        }
    }

</style>
