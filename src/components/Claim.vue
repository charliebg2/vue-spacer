<template>
<div class="claimWrapper">
    <h1 class="claim">SPACER</h1>
    <p class="subclaim">Lorem ipsum dolor sit amet consectetur adipisicing elit. 
        Quam nesciunt in eius eaque voluptatem sunt, ab, 
    </p>

    <p class="subclaim">Lorem, ipsum dolor sit amet consecteturh</p>
</div>
</template>

<script>
export default {
    name: 'Claim',
}
</script>

<style lang="scss" scoped>

.claimWrapper{
    display:flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    text-align: center;

    .claim{
        font-size: 50px;
        margin: 0;
    }
    .subclaim{
        font-size: 13px;
        margin: 13px 0 0 0;
    }
}

</style>
