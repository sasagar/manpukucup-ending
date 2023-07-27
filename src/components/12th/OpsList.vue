<script setup>
import OpsContainer from './parts/OpsContainer.vue';
import ops from "../../assets/json/12th/ops.json";
import { computed, onMounted, ref } from 'vue';
const opsArr = ops.ops;

const all = [...opsArr];
const counter = ref(0);

const displayArr = computed(() => {
    const i = counter.value * 12;
    return all.slice(i, i + 12);
});

const emit = defineEmits(['endOps']);
const emitter = () => {
    emit('endOps', true);
}

const isShow = ref(true);
const _sleep = (ms) => new Promise((resolve) => setTimeout(resolve, ms));

const teamTimer = function() {
    const timer =window.setInterval(async () => {
        isShow.value = false;
        if (((counter.value + 1) * 8) > all.length) {
            console.log('clear');
            clearInterval(timer);
            emitter();
            return;
        }
        await _sleep(500);
        console.log(all.length);        
        counter.value++;
        console.log(counter.value * 8);
        console.log(counter.value);

        isShow.value = true;
    },7000);
}
onMounted(() => {
    teamTimer();
});
</script>

<template>
    <div>
        <h2>まんぷく杯運営チーム</h2>
        <div id="team-list">
            <Transition name="fade" appear>
                <div id="team-list-container" v-if="isShow">
                    <OpsContainer v-for="team in displayArr" :props="team" :key="team.name"/>
                </div>
            </Transition>
        </div>
    </div>
</template>

<style lang="scss" scoped>
#team-list {
    width: 100%;
    height: 80%;
    display: flex;
    justify-content: center;
    align-items: center;
    margin-top: 30px;

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

h2 {
    font-family: var(--font-family-s1);
    font-size: 60px;
    text-align: center;
    padding-top: 100px;
}

</style>