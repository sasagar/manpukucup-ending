<script setup>
defineProps({
    props: Object
});
</script>

<template>
    <div class="ops-container" :class="props.push">
        <div class="ops-background-color">
            <h2>{{ props.name }}</h2>
            <h3>{{ props.futatsuna }}</h3>
        </div>
    </div>
</template>

<style lang="scss" scoped>
.ops-background-color {
    background-blend-mode: multiply;
    // filter: brightness(130%);
    width: 100%;
    height: 100%;
}

.ops-container {
    background-repeat: no-repeat;
    background-size: cover;
    width: 500px;
    aspect-ratio: 7/2;
    position: relative;
    filter: drop-shadow(0 0 10px #fff);

    &.ops {
        background-image: url('@/assets/images/12th/ops.png');
        // .team-background-color{
                // background-color: rgba(255,255,255,.3);
        // }

        h2 {
            color: #000;
            // filter: drop-shadow(0 0 5px #fff);
        }

        h3 {
            color: #000;
            // filter: drop-shadow(0 0 3px #fff);
        }

        .team-members {
            span {
                color: #000;
                // filter: drop-shadow(0 0 2px #fff);
            }
        }
    }

    h2 {
        position: absolute;
        top: 40px;
        width: 100%;
        font-family: var(--font-family-s1);
        font-size: 45px;
        text-align: center;
    }

    h3 {
        position: absolute;
        top: 10px;
        left: 10px;
        font-size: 22px;
    }
}
</style>