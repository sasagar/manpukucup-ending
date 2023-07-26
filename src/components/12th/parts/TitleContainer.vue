<script setup>
import titleImg from "../../../assets/images/12th/manpukucup_12.png";
console.log(titleImg);
document.getElementById("manpukucup_title").src = titleImg;
</script>

<template>
    <img id="manpukucup_title" alt="第12回まんぷく杯" rel="preload">
</template>

<style lang="scss" scoped>
img {
    position: absolute;
    top: 40%;
    left: 50%;
    transform: translateX(-50%) translateY(-50%);
    width: 900px;
    height: auto;
}
</style>