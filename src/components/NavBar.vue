<template>
  <v-app-bar app color="black" dark flat class="px-12" elevate-on-scroll scroll-target="#scrolling-techniques-7">
    <v-spacer></v-spacer>
    <v-btn text @click="scroll('home')" class="text-light-blue-lighten-2" size="large">Home</v-btn>
    <v-btn text @click="scroll('about')" size="large">關於我</v-btn>
    <v-btn text @click="scroll('portfolio')" size="large">作品</v-btn>
  </v-app-bar>
</template>

<script>
export default {
    methods: {
        scroll(refName) {
            const element = document.getElementById(refName)
            element.scrollIntoView({behavior: 'smooth'})
        }
    }
}
</script>

<style>
</style>