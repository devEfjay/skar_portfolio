<script>
export default {
     data(){
    return {
      nav: false,
      hamHover: false,
      hamClick: false
    }
    },
    methods: {
        convertS(value){
            return value.split(' ').join('')
        },handleHamClick(){
            this.nav = !this.nav;
            this.hamClick = !this.hamClick;
    },
    handleHamHover(){
            this.hamHover = !this.hamHover;
    },
    handleOverlay(){
            this.nav = !this.nav;
            this.hamClick = !this.hamClick;        
    }
    },
    computed: {

        cssVars(){
            let base = "/pics/clients_work/";
            let cBase = "url(" + base ;

            
            return [
                {
                    name: "Portrait",
                    url: base+"portrait/1.webp",
                    styles: [
                        {'--bg-image': cBase+"portrait/1.webp)"}
                    ]
                }
                ,
                {
                    name: "Concept Art",
                    url: base+"concept_art/1.webp",
                    styles: [
                        {'--bg-image': cBase+"concept_art/1.webp)"}
                    ]
                },
                {
                    name: "Character Design",
                    url: base + "character_design/1.webp",
                    styles: [
                        {'--bg-image': cBase+"character_design/1.webp)"}
                    ],
                },
                {
                    name: "Illustration",
                    url: base + "illustration/1.webp",
                    styles: [
                        {'--bg-image': cBase+"illustration/1.webp)"}
                    ],
                },
                {
                    name: "Comics Project",
                    url: base + "comics_project/1.webp",
                    styles: [
                        {'--bg-image': cBase+"comics_project/1.webp)"}
                    ]
                }, 
            ];
        }
        
    }
}
</script>

<template>
<transition name="fade">
    <div class="controller">
        
         <NavBar :show="true" :x="false" v-if="$device.isDesktopOrTablet"></NavBar>

    <NavBar :show="nav" :x="nav" v-if="$device.isMobile"></NavBar>
    <MobNavBar v-if="$device.isMobile" ></MobNavBar>

    <transition name="overlayTrans"> 
      <div class="overlay" v-show="nav" @click="handleOverlay()"></div>
    </transition>
    <Hamburger v-if="$device.isMobile" :ham_hover="hamHover" :ham_click="hamClick" @hamHoverAction="handleHamHover()" @hamClickAction="handleHamClick()"/>
        
        <main class="main">
            <NuxtLink :to="{
                name:'client_arts', 
                params: {
                    activeComponent: convertS(item.name), 
                    weird: 'hello'
                    }
                }" 
                v-for="(item, index) in cssVars" 
                :key="index" 
                class="card" 
                :style="item.styles" 
                :rel="item.name">
                
                <img 
                    :src="item.url" 
                    alt="images for categories" 
                    :class="['card__image']"    
                    height="100%" 
                    width="100%" 
                />
                <div class="card__border">
                    <i class="card__text">{{ item.name }}</i>
                </div>
            </NuxtLink>
        </main>
    </div>
</transition>
</template>

<style lang="scss" scoped>
   
</style>