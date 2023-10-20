<template>
    <v-app-bar app color= "white" dark flat class="px-40">
        <v-btn>
            <v-icon color="black" left class="mr-2">fas fa-signature</v-icon>Hugo Jarland - Portfolio
        </v-btn>
        <v-spacer></v-spacer>
        <v-btn text @click="scroll('home')" class="text-black">Home</v-btn>
        <v-btn text @click="scroll('about')" class="text-black">About</v-btn>
        <v-btn text @click="scroll('portfolio')" class="text-black">Portfolio</v-btn>
        <v-btn text @click="scroll('contact')" class="text-black">Contact</v-btn>
    </v-app-bar>
</template>

<script>
export default {
    methods: {
        scroll(refName) {
            const element = document.getElementById(refName);
            element.scrollIntoView({behavior: "smooth"});
        }
    }
}
</script>

<style>
</style>