<template>
    <div class="building">
        <img src="@/assets/background.png" class="background" ref="background" v-on:click="background"/>
        <img src="@/assets/station.png" class="station" ref="station" v-on:click="station"/>
        <img src="@/assets/girl.png" class="girl" ref="girl" v-on:click="girl"/>
        <img src="@/assets/vending_machine.png" class="vending_machine" v-on:click="vendor"/>
        <img src="@/assets/signboard.png" class="signboard" v-on:click="signboard"/>
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
        overflow: scroll;
        margin:0 auto;
        position: relative;
        justify-content: center;
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
        width: auto;
        height: auto;
        position: absolute;
        bottom: -180px;
        left: 2800px;
    }
    .building .vending_machine {
        width: auto;
        height: auto;
        position: absolute;
        bottom: -180px;
        left: 2000px;
    }
    .building .signboard {
        width: auto;
        height: auto;
        position: absolute;
        bottom: -180px;
        left: 3400px;
    }
    /* .building .girl {
        height: 40%;
        position: absolute;
        bottom: 25%;
    }
    .building .vending_machine {
        height: 300px;
        position: absolute;
        bottom: 25%;
        left: 100px;
    }
    .building .signboard {
        height: 300px;
        position: absolute;
        bottom: 25%;
        right: 100px;
    } */
</style>
<script>
export default {
    // transition: {
    //     name: "fade_in"
    // }
    mounted() {
        const girl = this.$refs.girl
        girl.scrollIntoView(
            {
                behavior: "instant",
                block: "center",
                inline: "center"
            }
        )
        window.addEventListener("scroll", this.onScroll)
    },
    destroyed() {
        window.removeEventListener("scroll", this.onScroll)
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
        onScroll: function() {
            const background = this.$refs.background
            const station = this.$refs.station
            console.log("aaa")
        }
    },
}
</script>
