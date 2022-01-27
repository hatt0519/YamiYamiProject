<template>
    <div class="building">
        <img src="@/assets/background.webp" class="background" ref="background" v-on:click="background"/>
        <img src="@/assets/station.webp" class="station" ref="station" v-on:click="station"/>
        <img src="@/assets/girl.webp" class="girl" ref="girl" v-on:click="girl"/>
        <img src="@/assets/vending_machine.webp" class="vending_machine" v-on:click="vendor"/>
        <img src="@/assets/signboard.webp" class="signboard" v-on:click="signboard"/>
    </div>
</template>

<style scoped>
    /* .fade_in-enter {
        animation-delay: 3.0s;
    } */
    /* .fade_in-enter-active {
        animation-timing-function:ease-in;
        animation: enter 3.0s;
    } */
    @keyframes enter {
        0% {
        opacity: 0;
        }
        100% {
        opacity: 100;
        }
    }
    .building {
        width: 1480px;
        height: 900px;
        overflow-x: scroll;
        overflow-y: hidden;
        margin:0 auto;
        position: relative;
    }
    .building .background {
        width: 5509px;
        height: 1440px;
        position: absolute;
        background: linear-gradient(white, black);
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
</style>
<script>
export default {
    // transition: {
    //     name: "fade_in"
    // }
    mounted() {
        this.focusGirl()
        window.addEventListener("scroll", this.onScroll)
        window.addEventListener("resize", this.onResizeWindow)
    },
    destroyed() {
        window.removeEventListener("scroll", this.onScroll)
        window.removeEventListener("resize", this.onResizeWindow)
    },
    methods: {
        girl: function(event) {
            alert("女の子だよ")
        },
        vendor: function(event) {
            alert("自販機だよ")
        },
        signboard: function(event) {
            alert("看板だよ")
        },
        station: function(event) {
            alert("駅だよ")
        },
        background: function(event) {
            alert("背景だよ")
        },
        focusGirl: function() {
            const girl = this.$refs.girl
            girl.scrollIntoView(
                {
                    behavior: "instant",
                    block: "center",
                    inline: "center"
                }
            )
        },
        onScroll: function() {
            const background = this.$refs.background
            const station = this.$refs.station
            console.log("aaa")
        },
        onResizeWindow() {
            this.focusGirl()
        }
    },
}
</script>
