<script setup>
const state = defineProps({
    props: Boolean
});
</script>

<template>
    <div class="charactor-container" :class="{active: state.props}">
        <img src="/images/12th/shan.png" alt="しゃん" id="shan" class="charactor" rel="preload">
        <img src="/images/12th/yoyomi.png" alt="よよみ" id="yoyomi" class="charactor" rel="preload">
        <img src="/images/12th/hinanu.png" alt="ひなぬー" id="hinanu" class="charactor" rel="preload">
        <img src="/images/12th/2basa.png" alt="2BASA" id="tsubasa" class="charactor" rel="preload">
        <img src="/images/12th/sasapiyo.png" alt="ささぴよ" id="sasapiyo" class="charactor" rel="preload">
        <img src="/images/12th/midodo.png" alt="みどど" id="midodo" class="charactor" rel="preload">
        <img src="/images/12th/gazooo0.png" alt="がずー" id="gazooo0" class="charactor" rel="preload">
        <img src="/images/12th/manpuku.png" alt="まんぷくちゃん" id="manpuku" class="charactor" rel="preload">
    </div>
</template>

<style lang="scss" scoped>
.charactor-container {
    position: absolute;
    left: 0;
    top: 0;
    width: 100%;
    height: 100%;
    overflow: hidden;

    .charactor {
        position: absolute;
        height: calc(1080px * 0.35);
        width: auto;
        transition: all .5s ease-in-out;
    }
    #shan {
        bottom: 700px;
        left: -30px;
    }
    #yoyomi {
        bottom: 470px;
        left: 0;
    }
    #hinanu {
        bottom: 240px;
        left: 20px;
    }
    #tsubasa {
        bottom: -20px;
        left: 90px;
    }
    #sasapiyo {
        bottom: 700px;
        right: -30px;
    }
    #midodo {
        bottom: 470px;
        right: 10px;
    }
    #gazooo0 {
        bottom: 240px;
        right: 10px;
    }
    #manpuku {
        bottom: -20px;
        right: 50px;
    }

    &.active {
        #shan {
            bottom: -90px;
            left: 0;
            animation: jump 5s linear normal infinite .5s;
        }
        #yoyomi {
            bottom: -90px;
            left: 230px;
            animation: jump 5s linear normal infinite 2s;
        }
        #hinanu {
            bottom: -90px;
            left: 490px;
            animation: jump 5s linear normal infinite 3s;
        }
        #tsubasa {
            bottom: -90px;
            left: 720px;
            animation: jump 5s linear normal infinite 3.5s;
        }
        #sasapiyo {
            bottom: -90px;
            right: 0;
             animation: jump 5s linear normal infinite 1s;
       }
        #midodo {
            bottom: -90px;
            right: 230px;
             animation: jump 5s linear normal infinite 4.5s;
       }
        #gazooo0 {
            bottom: -90px;
            right: 430px;
            animation: jump 5s linear normal infinite 2.5s;
        }
        #manpuku {
            bottom: -90px;
            right: 650px;
            animation: jump 5s linear normal infinite;
        }
    }
}

@keyframes jump {
    0% {
        transform: translateY(10px);
    }

    3% {
        transform: translateY(-40px);
    }

    5% {
        transform: translateY(5px);
    }

    6% {
        transform: translateY(-3px);
    }
    
    7% {
        transform: transltateY(0);
    }

    98% {
        transform: translateY(0);
    }

    100% {
        transform: translateY(10px)
    }
    
}
</style>