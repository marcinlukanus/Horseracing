<template>
    <div class="container">
        <div class="row justify-content-center">
            <b-button
                v-if="!gameOver"
                @click="generateSuit()"
                variant="success"
                class="mr-3"
            >
                Draw Cards
            </b-button>

            <RulesModal class="ml-3" />
        </div>
        <div
            v-for="(horse, id) in horses"
            :key=id
        >
            <img :src=horse.card />
        </div>
    </div>
</template>

<script>
import RulesModal from './RulesModal.vue'
import Vue from 'vue'
import VueConfetti from 'vue-confetti'

Vue.use(VueConfetti)

export default {
    components: {
        RulesModal,
    },
    data: () => ({
        horses: {
            club: {
                id: 0,
                card: require('../assets/horses/ACEC.png'),
                position: 0
            },
            diamond: {
                id: 1,
                card: require('../assets/horses/ACED.png'),
                position: 0
            },
            heart: {
                id: 2,
                card: require('../assets/horses/ACEH.png'),
                position: 0
            },
            spade: {
                id: 3,
                card: require('../assets/horses/ACES.png'),
                position: 0
            }
        },
        finishLine: 10,
        gameOver: false,
        suits: ['club', 'diamond', 'heart', 'spade']
    }),
    methods: {
        checkGameOver(suit) {
            if (this.horses[suit].position + 1 === this.finishLine) {
                this.gameOver = true

                this.$bvToast.toast('It\'s over! It\'s all over!', {
                    title: `${suit.toUpperCase()}S WINS!`,
                    variant: 'success',
                    solid: true,
                    toaster: 'b-toaster-top-center'
                })

                this.$confetti.start({
                        particlesPerFramne: .05,
                        defaultDropRate: 20,
                        windSpeedMax: 0,
                        particles: [
                            {
                                size: 30
                            },
                        ],
                    })
            }
        },
        generateSuit() {
            let suit = this.suits[Math.floor(Math.random() * this.suits.length)]

            this.checkGameOver(suit)     
            this.horses[suit].position++     

            console.log('club: ' + this.horses.club.position)
            console.log('diamond: ' + this.horses.diamond.position)
            console.log('heart: ' + this.horses.heart.position)
            console.log('spade: ' + this.horses.spade.position)
            console.log('-----------------------')

            // return this.horses[suit].position++
        }
    }
}
</script>