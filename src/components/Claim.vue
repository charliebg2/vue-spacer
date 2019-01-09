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


.claimWrapper{
    display:flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    text-align: center;

    .claim{
        font-size: 50px;
        margin: 0;
        @include ipad{
            font-size: 80px;
        }
        @include desktop{
            font-size: 100px;   
        }
    }
    .subclaim{
        font-size: 13px;
        margin: 20px 0 0 0;

        font-weight: 400;

        @include ipad{
            letter-spacing: 1px;
            font-size: 17px;
            line-height: 1;
                    width: 500px;
        }
    }
}

</style>
