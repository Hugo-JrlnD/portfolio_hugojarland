<template>
    <v-app-bar app color= "white" dark flat class="px-40">
        <v-btn>
            <v-icon color="black" left class="mr-2">fas fa-signature</v-icon>Hugo Jarland - Portfolio
        </v-btn>
        <v-spacer></v-spacer>
        <v-btn text @click="scroll('about')" class="text-black">About</v-btn>
        <v-btn text @click="scroll('projects')" class="text-black">Projects</v-btn>
        <v-btn text @click="scroll('contact')" class="text-black">Contact</v-btn>
        <v-btn text @click="DisplayCV()" class="text-black">CV</v-btn>
    </v-app-bar>
</template>

<script>
export default {
    methods: {
        scroll(refName) {
            const element = document.getElementById(refName);
            element.scrollIntoView({behavior: "smooth"});
        },
        DisplayCV() {
             window.open("https://publuu.com/flip-book/275027/643894", "_blank");
        },
    }  
}
</script>

<style>
</style>