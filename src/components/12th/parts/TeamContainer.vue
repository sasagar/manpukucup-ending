<script setup>
defineProps({
    props: Object
});
</script>

<template>
    <div class="team-container" :class="props.push">
        <div class="team-background-color">
            <h2>{{ props.name }}</h2>
            <h3>{{ props.futatsuna }}</h3>
            <div class="team-members">
                <span v-for="member in props.members" :key="member.name">{{ member.name }}</span>
            </div>
        </div>
    </div>
</template>

<style lang="scss" scoped>
.team-background-color {
    background-blend-mode: multiply;
    // filter: brightness(130%);
    width: 100%;
    height: 100%;
}

.team-container {
    background-repeat: no-repeat;
    background-size: cover;
    width: 500px;
    aspect-ratio: 7/2;
    position: relative;

    &.umi {
        background-image: url('@/assets/images/12th/umi.png');
        .team-background-color{
                background-color: rgba(255,255,255,.3);
        }

        h2 {
            color: #000;
            filter: drop-shadow(0 0 5px #fff);
        }

        h3 {
            color: #000;
            filter: drop-shadow(0 0 3px #fff);
        }

        .team-members {
            span {
                color: #000;
                filter: drop-shadow(0 0 2px #fff);
            }
        }
    }

    &.hanabi {
        background-image: url('@/assets/images/12th/hanabi.png');
        .team-background-color{
                background-color: rgba(0,0,0,.3);
        }
        h2 {
            color: #fff;
            filter: drop-shadow(0 0 5px #000);
        }

        h3 {
            color: #fff;
            filter: drop-shadow(0 0 3px #000);
        }

        .team-members {
            span {
                color: #fff;
                filter: drop-shadow(0 0 2px #000);
            }
        }
    }

    &.bbq {
        background-image: url('@/assets/images/12th/bbq.png');
        .team-background-color{
                background-color: rgba(255,255,255,.3);
        }
        h2 {
            color: #000;
            filter: drop-shadow(0 0 5px #fff);
        }

        h3 {
            color: #000;
            filter: drop-shadow(0 0 3px #fff);
        }

        .team-members {
            span {
                color: #000;
                filter: drop-shadow(0 0 2px #fff);
            }
        }
    }


    h2 {
        position: absolute;
        top: 25px;
        width: 100%;
        font-family: var(--font-family-s1);
        font-size: 35px;
        text-align: center;
    }

    h3 {
        position: absolute;
        top: 10px;
        left: 10px;
        font-size: 18px;
    }
    
    .team-members {
        width: calc(100% - 60px);
        position: absolute;
        bottom: 10px;
        font-family: var(--font-family-s1);
        display: flex;
        flex-wrap: wrap;
        justify-content: center;
        margin-left: 30px;
        margin-right: 30px;
        column-gap: 20px;
        span {
            font-size: 16px;
        }
    }
}
</style>