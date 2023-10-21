<template>
  <v-app>
    <v-main>
      <NavBar/>
      <v-container fluid>
        <div class="head">
            <v-row>
              <v-col cols="5">
                <div style="position: relative" class="mt-0">
                  <h1 class="text-black">Hello, I am Hugo Jarland</h1>
                  <span class="text-black">A Creative Technologist Engineer Student</span><br />
                </div>
              </v-col>
            </v-row>
        </div>
        <v-col cols="12" id="about">
          <div>
            <v-row>
              <v-col cols="12" sm="6">
                  <v-img src="pdp-rond.jpg" max-height="300"></v-img>
              </v-col>
              <v-col cols="12" sm="6">
                <h1 class="mt-8">About Me</h1>
                <div style="width: 80%;">
                  <h4 class="mt-4" style="text-align: justify;">I am a Creative Technology Student at the De Vinci Innovation Center. As part of the 'Resilient Future' 
                    innovation group, I am particularly interested in more sustainable ways of living, using low and high technologies. 
                    This year, I focus on types of ecological agriculture that could be simply reproduced at home such as hydroponics and aquaponics.</h4>
              </div>
              </v-col>
            </v-row>
          </div>
        </v-col>

        <br>
        <br>
        <v-divider></v-divider>
        <v-col cols="12" sm="12" id="projects">
          <h1 class="mt-8" style="text-align: center;">Projects</h1>
          <br>
          <div class="d-flex justify-center mb-6">
            <v-btn class="mr-2" variant="tonal" @click="filterItems('Agriculture')">Agriculture</v-btn>
            <v-btn class="mr-2" variant="tonal">Architecture</v-btn>
            <v-btn class="mr-2" variant="tonal">Leather</v-btn>
            <v-btn class="mr-2" variant="tonal">Others</v-btn>
          </div>
        </v-col>

        <v-col cols="12" class="imgHover">
          <v-row class="fill-height" align="center" justify="center">

            <v-col cols="3" md="4" :class="{'is-active': items[1].category === category}">
              <v-hover v-slot="{ isHovering, props }">
                <v-card :elevation="isHovering ? 12 : 2" :class="{'on-hover' : isHovering}" v-bind="props">
                  <v-img :src="items[0].img" height="300px" cover text @click="DisplayLarge(this.items[0].imgLarge)"></v-img>
                  <v-card-title text @click="goToDvicAquaponics()">{{ "The Aquaponic Platform" }}</v-card-title>
                  <v-card-subtitle style="white-space: pre-line">{{ "An educational, modular and adjustable aquaponic system to reconnect people with food production" }}</v-card-subtitle>
                </v-card>
              </v-hover>
            </v-col>

            <v-col cols="3" md="4" :class="{'is-active': items[1].category === category}">
              <v-hover v-slot="{ isHovering, props }">
                <v-card :elevation="isHovering ? 12 : 2" :class="{'on-hover' : isHovering}" v-bind="props">
                  <v-img :src="items[6].img" height="300px" cover text @click="DisplayLarge(this.items[6].img)"></v-img>
                  <v-card-title text @click="goToDvicPFS()">{{ "Passive Filtration System" }}</v-card-title>
                  <v-card-subtitle style="white-space: pre-line">{{ "Manufacturing of a low maintenance filtration system and passive filters in order to save energy" }}</v-card-subtitle>
                </v-card>
              </v-hover>
            </v-col>

            <v-col cols="3" md="4" :class="{'is-active': items[1].category === category}">
              <v-hover v-slot="{ isHovering, props }">
                <v-card :elevation="isHovering ? 12 : 2" :class="{'on-hover' : isHovering}" v-bind="props">
                  <v-img :src="items[1].img" height="300px" cover text @click="DisplayLarge(this.items[1].img)"></v-img>
                  <v-card-title>{{ "The Hydroponic System" }}</v-card-title>
                  <v-card-subtitle style="white-space: pre-line">{{ "A low maintenance hydroponic system using a urine-based fertiliser and capilarity to grow plants" }}</v-card-subtitle>
                </v-card>
              </v-hover>
            </v-col>

            <v-col cols="3" md="4" :class="{'is-active': items[1].category === category}">
              <v-hover v-slot="{ isHovering, props }">
                <v-card :elevation="isHovering ? 12 : 2" :class="{'on-hover' : isHovering}" v-bind="props">
                  <v-img :src="items[3].img" height="300px" cover text @click="DisplayLarge(this.items[3].img)"></v-img>
                  <v-card-title text @click="goToDvicTLP()">{{ "The Leather Page" }}</v-card-title>
                  <v-card-subtitle style="white-space: pre-line">{{ "A leather book protection with an integrated bookmark to keep your books perfect and never lose track of your story" }}</v-card-subtitle>
                </v-card>
              </v-hover>
            </v-col>

            <v-col cols="3" md="4" :class="{'is-active': items[1].category === category}">
              <v-hover v-slot="{ isHovering, props }">
                <v-card :elevation="isHovering ? 12 : 2" :class="{'on-hover' : isHovering}" v-bind="props">
                  <v-img :src="items[2].img" height="300px" cover text @click="DisplayLarge(this.items[2].imgLarge)"></v-img>
                  <v-card-title>{{ "The New Green Wall" }}</v-card-title>
                  <v-card-subtitle style="white-space: pre-line">{{ "Creation of a low maintenance and modular green wall to reconnect people with nature and increase their creativity" }}</v-card-subtitle>
                </v-card>
              </v-hover>
            </v-col>

            <v-col cols="3" md="4" :class="{'is-active': items[1].category === category}">
              <v-hover v-slot="{ isHovering, props }">
                <v-card :elevation="isHovering ? 12 : 2" :class="{'on-hover' : isHovering}" v-bind="props">
                  <v-img :src="items[8].img" height="300px" cover text @click="DisplayLarge(this.items[8].img)"></v-img>
                  <v-card-title>{{ "Upcoming projects" }}</v-card-title>
                  <v-card-subtitle style="white-space: normal; word-wrap: break-word">
                    {{ "- The portable coat rack" }}
                    <br>
                    {{ "- The cigarette case with integrated ashtray" }}
                    <br>
                    {{ "- The sock hook" }}
                  </v-card-subtitle>
                </v-card>
              </v-hover>
            </v-col>

          </v-row>
        </v-col>
        <br>

        <v-divider></v-divider>
        <v-col col="12" sm="12" class="px-16" id="contact">
          <v-row>
            <v-col cols="12" sm="4">
              <div class="child">
                <h1>Contact info</h1>
                <v-divider></v-divider>
                <v-btn icon="fas fa-map-marker-alt" class="mt-2" variant="outlined"></v-btn><br />
                <span class="text-caption">59 rue de la République - 95240 - Cormeilles-en-Parisis</span><br />
                <v-btn icon="fas fa-phone-alt" class="mt-2" variant="outlined"></v-btn><br />
                <span class="text-caption">+33 6 95 78 32 78</span><br />
                <v-btn icon="fas fa-envelope" class="mt-2" variant="outlined"></v-btn><br />
                <span class="text-caption">hugo.jarland@edu.devinci.fr</span><br />
                <v-btn icon="fab fa-linkedin-in" class="mt-2" variant="outlined" href="https://www.linkedin.com/in/hugo-jarland-9a4a9a1bb/"></v-btn><br />
                <span class="text-caption">Hugo Jarland</span><br />
              </div>
              
            </v-col>
            <v-col cols="12" sm="8">
              <h1 class="mt-8">For more information</h1>
              <v-divider></v-divider>
              <span class="text-caption">
                The DVIC is the research and innovation center of the Leonard de Vinci University pole located in La Défense. 
                It is a space filled with creativity and engineering. It is the ideal place to bring to life the projects that are close to my heart 
                and to develop many skills in computer science, electronics, manufacturing processes, design, public speaking, low-technologies, 
                biomaterials and much more. Deeply sensitive to climate issues, I joined the Resilient Futures innovation Group which focuses on 
                biomaterials and low-technologies to develop more ecological and resilient projects. Therefore, I joined the DVIC with a desire to 
                learn new skills while developing concrete ecological projects.
              </span>
              <h1 class="mt-8">Pictures</h1>
              <v-divider></v-divider>
              <v-container>
                <v-row justify="center" align="center">
                  <v-col cols="3" sm="6" md="4">
                    <v-card class="my-2">
                      <v-img :src="items[5].img" height="100px" width="100%" />
                    </v-card>
                  </v-col>
                  <v-col cols="3" sm="6" md="4">
                    <v-card class="my-2">
                      <v-img :src="items[6].img" height="100px" width="100%" />
                    </v-card>
                  </v-col>
                  <v-col cols="3" sm="6" md="4">
                    <v-card class="my-2">
                      <v-img :src="items[7].img" height="100px" width="100%" />
                    </v-card>
                  </v-col>
                </v-row>
              </v-container>
            </v-col>
          </v-row>
        </v-col>

      </v-container>
      <FooterView />
    </v-main>
  </v-app>
</template>

<script>
import { defineComponent } from 'vue';

import NavBar from './components/NavBar.vue';
import FooterView from './components/FooterView.vue';

export default defineComponent({
  name: 'App',
  methods: {
    goToDvicAquaponics() {
      window.open("https://dvic.devinci.fr/projects/aquaponic-system", "_blank");
    },
    goToDvicTLP() {
      window.open("https://dvic.devinci.fr/quickstarter/the-leather-page", "_blank");
    },
    goToDvicPFS() {
      window.open("https://dvic.devinci.fr/tutorial/passive-filters", "_blank");
    },
    DisplayLarge(photo) {
      window.open(photo, "_self");
    },
    filterItems(category) {
      const categoryInfo = {
        Agriculture: ['i3_test.jpg', 'i4.jpg'],
        Architecture: ['i5.png'],
        Others: ['i6.jpg'],
      };
      return categoryInfo[category];
    },
  },
  setup(){
    return {
      slider2: 50,

items: [
  {
    img: "i3_test.jpg",
    imgLarge: "i3.jpg",
    category: "Agriculture",
  },
  {
    img: "i4.jpg",
    category: "Agriculture",
  },
  {
    img: "i5.png",
    imgLarge: "i5_large.jpg",
    category: "Architecture",
  },
  {
    img: "i6.jpg",
    category: "Others",
  },
  {
    img: "i9.jpg",
  },
  {
    img: "i8.png",
  },
  {
    img: "i10.png",
  },
  {
    img: "i11.png",
  },
  {
    img: "i12.png",
  },
  {
    img: "photo_profil.png",
  },
],
    }
  },
  components: {
    NavBar,
    FooterView
},
  data: () => ({
    //
  }),
});
</script>

<style scoped>
.v-container{
  padding: 0px 0;
}
.head {
  position: relative;
  text-align: center;
  padding: 12px;
  margin-bottom: 6px;
  height: 200px;
  width: 100%;
  color: white;
}
.head:before{
  content: " ";
  position : absolute;
  top: 0;
  left: 0;
  height: 50%;
  width : 50%;
  background: rgb(220, 220, 220);
}
.head:after{
  content: " ";
  position : absolute;
  top: 0;
  right: 0;
  height: 50%;
  width : 50%;
  background: rgb(220, 220, 220);
}
.egg{
  display: block;
  margin-left: 100px;
  margin-top: 50px;
  width: 356px;
  height: 300px;
  background-color: #e5e5e5;
  border-radius: 50% 50% 50% 50% / 60% 60% 40% 0%;
}
.first {
  width: 100%;
  height: 280px;
  text-align: center;
  padding: 2rem 2rem;
}
.child {
  display: inline-block;
  padding: 2rem 1rem;
  vertical-align: middle;
  text-align: center;
  margin-right: 8px;
}
.imgHover {
  padding: 0 200px;
}
.pre {
  width: 100%;
  height: 380px;
  text-align: center;
  padding: 0 200px;
  background-color: #F5F5F5;
}
.hire {
  width: 100%;
  height: 200px;
  padding: 0 200px;
  background-color: #E9E9E9;
  margin-top: -24px;
}

</style>

