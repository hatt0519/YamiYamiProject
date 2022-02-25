<template>
    <div class="building" ref="building">
        <img src="/background_rear.webp" class="background all" ref="background_rear" v-on:click="background" v-bind:style="backgroundRearStyle"/>
        <img src="/background_front.webp" class="background all" ref="background_front" v-on:click="background" v-bind:style="backgroundFrontStyle" />
        <img src="/station.webp" class="station all" ref="station" v-on:click="station"/>
        <img src="/girl.webp" class="girl all" ref="girl" v-on:click="girl"/>
        <img src="/vending_machine.webp" class="vending_machine all" v-on:click="vendor"/>
        <img src="/signboard.webp" class="signboard all" v-on:click="signboard"/>
        <div class="character_container">
            <img src="/walk_sample.gif" ref="walk" class="walk_character" v-on:click="walkCharacter"/>
        </div>
    </div>
</template>

<style scoped>
    .tv-enter-active {
        animation-timing-function:ease-in;
        animation: station-in 4.0s;
    }
    @keyframes station-in {
        0% {
            opacity: 0;
            transform: scale(0.1);
        }
        50% {
            opacity: 0;
        }
        80% {
            opacity: 0.2;
        }
        90% {
            opacity: 0.4;
        }
        100% {
            opacity: 1;
            transform: scale(1);
        }
    }
    .building {
        width: 100%;
        height: 900px;
        overflow-x: scroll;
        overflow-y: hidden;
        margin:0 auto;
        position: absolute;
    }
    .building .background {
        width: 5509px;
        height: 1440px;
        position: absolute;
    }
    .building .station {
        width: 5509px;
        height: 1440px;
        position: absolute;
    }
    .building .girl {
        width: 187px;
        height: 467px;
        position: absolute;
        bottom: -180px;
        left: 2800px;
    }
    .building .vending_machine {
        width: 347px;
        height: 529px;
        position: absolute;
        bottom: -180px;
        left: 2000px;
    }
    .building .signboard {
        width: 462px;
        height: 522px;
        position: absolute;
        bottom: -180px;
        left: 3400px;
    }
    .building .walk_character {
        width: 300px;
        height: auto;
        position: absolute;
        bottom: -180px;
        left: calc(5509px - 300px);
        animation: walk normal linear 20s infinite;
    }
    @keyframes walk {
        0% {
            transform: translateX(0px);
        }
        100% {
            transform: translateX(-5509px);
        }
    }
    .building .character_container:hover .walk_character{
        animation-play-state: paused;
    }
</style>
<script lang="ts">
import Vue from 'vue'
interface Style {
    transform: string
}
interface ScrollState {
    lastScrollX: number
    x: number
}
export default Vue.extend({
    data: () => ({
        backgroundFrontStyle: {
            transform: "translateX(0px)"
        },
        backgroundRearStyle: {
            transform: "translateX(0px)"
        },
        backgroundFrontScrollState: {
            lastScrollX: 0,
            x: 0
        },
        backgroundRearScrollState: {
            lastScrollX: 0,
            x: 0
        }
    }),
    mounted() {
        this.focusGirl();
        (this.$refs.building as Element).addEventListener("scroll", this.onScroll)
        window.addEventListener("resize", this.onResizeWindow)
    },
    destroyed() {
        (this.$refs.building as Element).removeEventListener("scroll", this.onScroll)
        window.removeEventListener("resize", this.onResizeWindow)
    },
    methods: {
        girl: function(event: Event) {
            alert("女の子だよ")
        },
        vendor: function(event: Event) {
            alert("自販機だよ")
        },
        signboard: function(event: Event) {
            alert("看板だよ")
        },
        station: function(event: Event) {
            alert("駅だよ")
        },
        background: function(event: Event) {
            alert("背景だよ")
        },
        walkCharacter : function(event: Event) {
        },
        focusGirl: function() {
            const girl = this.$refs.girl as Element
            girl.scrollIntoView(
                {
                    block: "center",
                    inline: "center"
                }
            )
        },
        onScroll: function() {
            const frontVerocity = 0.2
            const frontScrollX = window.pageXOffset || this.$el.scrollLeft
            let frontX = 0
            if(this.$data.backgroundFrontScrollState.lastScrollX > frontScrollX) {
                frontX = this.$data.backgroundFrontScrollState.x + frontVerocity
            } else {
                frontX = this.$data.backgroundFrontScrollState.x - frontVerocity
            }
            this.$data.backgroundFrontStyle.transform = `translateX(${frontX}px)`
            this.$data.backgroundFrontScrollState.lastScrollX = frontScrollX
            this.$data.backgroundFrontScrollState.x = frontX

            const rearVerocity = 0.1
            const rearScrollX = window.pageXOffset || this.$el.scrollLeft
            let rearX = 0
            if(this.$data.backgroundRearScrollState.lastScrollX > rearScrollX) {
                rearX = this.$data.backgroundRearScrollState.x + rearVerocity
            } else {
                rearX = this.$data.backgroundRearScrollState.x - rearVerocity
            }
            this.$data.backgroundRearStyle.transform = `translateX(${rearX}px)`
            this.$data.backgroundRearScrollState.lastScrollX = rearScrollX
            this.$data.backgroundRearScrollState.x = rearX
        },
        onResizeWindow() {
            this.focusGirl()
        }
    },
    head () {
        return {
            link: [
                {
                rel: 'preload',
                href: '/background_front.webp',
                as: 'image'
                },
                {
                rel: 'preload',
                href: '/background_rear.webp',
                as: 'image'
                }
            ]
        }
    }
})
</script>
