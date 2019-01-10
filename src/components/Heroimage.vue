<template>
    <div class="heroImage"></div>
</template>

<script>
export default {
    name: 'Heroimage',
}
</script>

<style lang="scss" scoped>


    .heroImage{
        background-repeat: no-repeat;
        background-position: 80% 0%;
        background-size: cover;
        justify-content: center;
        width: 100%;
        height: 100%;
        top: 0;
        z-index: -1;
        position: fixed;
        background-image: url('../../assets/heroimage.jpg');
    }

    .heroImage::after{
        position: absolute;
        content: '';
        top:0;
        left: 0;
        z-index: 1;
        width: 100%;
        height: 100vh;
        background: rgba (0,0,0, .2);
    }
</style>
