<script setup>
import TitleContainer from './parts/TitleContainer.vue';
import OpenCreditText from './parts/OpenCreditText.vue';
import CloseCreditText from './parts/CloseCreditText.vue';
import OpsContainer from './parts/OpsContainer.vue';
import { computed, onMounted } from 'vue';

const stateProps = defineProps({
    props: Boolean
});

const emit = defineEmits(['endCover']);
const emitter = () => {
    emit('endCover', true);
}

const state = computed(() => {
    return stateProps.props;
});

onMounted(() => {
    console.log(stateProps.props);
    if (state.value) {
        const timer = window.setTimeout(() => {
            emitter();
            clearTimeout(timer);
            return;
        },13000);
    }
});

const manpuku = {
    "futatsuna": "Presented by",
    "name": "まんぷくちゃん",
    "push": "ops"
}

</script>

<template>
    <div id="title">
        <TitleContainer />
        <template v-if="props">
            <OpenCreditText />
        </template>
        <template v-else>
            <CloseCreditText />
            <OpsContainer :props="manpuku" class="card" />
        </template>
    </div>
</template>

<style lang="scss" scoped>
#title {
    width: 100%;
    height: 100%;
    position: relative;
    .card {
        position: absolute;
        bottom: 40%;
        left: 70%;
        transform: translateX(-50%) rotate(-15deg);
    }
}

</style>