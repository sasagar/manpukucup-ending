<script setup>
import TeamContainer from './parts/TeamContainer.vue';
import extra from "../../assets/json/12th/extra.json";
import pair from "../../assets/json/12th/pair.json";
import solo from "../../assets/json/12th/solo.json";
import team from "../../assets/json/12th/team.json";
import { computed, onMounted, ref } from 'vue';
const extraArr = extra.extras;
const soloArr = solo.solos;
const pairArr = pair.pairs;
const teamArr = team.teams;

const all = [...extraArr, ...soloArr, ...pairArr, ...teamArr];
const counter = ref(0);

const displayArr = computed(() => {
    const i = counter.value * 12;
    return all.slice(i, i + 12);
});
const emit = defineEmits(['endTeams']);
const emitter = () => {
    emit('endTeams', true);
}

const isShow = ref(true);
const _sleep = (ms) => new Promise((resolve) => setTimeout(resolve, ms));

const teamTimer = function() {
    const timer = window.setInterval(async () => {
        isShow.value = false;
        await _sleep(500);
        console.log(all.length);
        console.log(counter.value * 12);        
        counter.value++;
        console.log(counter.value);

        isShow.value = true;

        if ((counter.value * 12) > all.length) {
            console.log('clear');
            clearInterval(timer);
            emitter();
            return;
        }
    },8000);
}
onMounted(() => {
    teamTimer();
});
</script>

<template>
    <div id="team-list">
        <Transition name="fade" appear>
            <div id="team-list-container" v-if="isShow">
                <TeamContainer v-for="team in displayArr" :props="team" :key="team.name" />
            </div>
        </Transition>
    </div>
</template>

<style lang="scss" scoped>
#team-list {
    width: 100%;
    height: 80%;
    display: flex;
    justify-content: center;
    align-items: center;

    #team-list-container {
        display: flex;
        flex-wrap: wrap;
        gap: 50px;
        justify-content: center;
        align-items: center;
    }
}
.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}

.fade-enter-active,
.fade-leave-active {
  transition: all .5s ease-in-out;
}
</style>