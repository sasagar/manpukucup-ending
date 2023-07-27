<script setup>
import { ref } from 'vue';
import CharactorContainer from './components/12th/parts/CharactorContainer.vue';
import OpenContainer from './components/12th/OpenContainer.vue';
import TeamsList from './components/12th/TeamsList.vue';
import PresentsList from './components/12th/PresentsList.vue';
import SupportersList from './components/12th/SupportersList.vue';
import OpsList from './components/12th/OpsList.vue';

const readyShow = ref(true);
const coverShow = ref(false);
const coverState = ref(true);
const teamsListShow = ref(false);
const presentsListShow = ref(false);
const supportersListShow = ref(false);
const opsListShow = ref(false);

const charactorState = ref(false);

const _sleep = (ms) => new Promise((resolve) => setTimeout(resolve, ms));


const start = async () => {
  console.log("start");
  readyShow.value = false;
  await _sleep(500);
  document.querySelector('#musicplayer').play();
  coverShow.value = true;
}

const endCover = async (res) => {
  console.log("endCover");
  if (res) {
    coverShow.value = false;
    charactorState.value = true;
    await _sleep(500);
    teamsListShow.value = true;
  }
}

const endTeams = async (res) => {
  console.log("endTeams");
  if (res) {
    teamsListShow.value = false;
    await _sleep(500);
    presentsListShow.value = true;
  }
}

const endPresents = async (res) => {
  console.log("endTeams");
  if (res) {
    presentsListShow.value = false;
    await _sleep(500);
    supportersListShow.value = true;
  }
}

const endSupporters = async (res) => {
  console.log("endTeams");
  if (res) {
    supportersListShow.value = false;
    await _sleep(500);
    opsListShow.value = true;
  }
}

const endOps = async (res) => {
  if (res) {
    opsListShow.value = false;
    coverState.value = false;
    charactorState.value = false;
    await _sleep(500);
    coverShow.value = true;
    console.log("endOps");
  }
}

</script>

<template>
  <audio id="musicplayer" autoplay onplay="console.log('autoplay')">
    <source src="/audio/SAMBA_30min.mp3" />
  </audio>
  <main>
    <Transition name="fade">
      <div id="ready" v-show="readyShow">
        <h2 @click="start()">Ready...?</h2>
      </div>
    </Transition>
    <CharactorContainer :props="charactorState" />
    <Transition name="fade" appear>
      <OpenContainer @endCover="endCover" v-if="coverShow" :props="coverState" />
    </Transition>

    <Transition name="fade" appear>
      <TeamsList @endTeams="endTeams" v-if="teamsListShow" />
    </Transition>
    
    <Transition name="fade" appear>
      <PresentsList @endPresents="endPresents" v-if="presentsListShow" />
    </Transition>
    
    <Transition name="fade" appear>
      <SupportersList @endSupporters="endSupporters" v-if="supportersListShow" />
    </Transition>
    
    <Transition name="fade" appear>
      <OpsList @endOps="endOps" v-if="opsListShow" />
    </Transition>
  </main>
</template>

<style lang="scss" scoped>
main {
  width: 100%;
  height: 100%;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}

.fade-enter-active,
.fade-leave-active {
  transition: all .5s ease-in-out;
}

#ready {
  width: 100%;
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  position: absolute;
  z-index: 100;
  h2 {
    font-family: var(--font-family-s1);
    font-size: 80px;
  }
}
</style>
