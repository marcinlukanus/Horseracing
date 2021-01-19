<template>
    <div class="container">
        <div class="row justify-content-center mb-4">
            <b-button
                v-if="!gameOver"
                @click="generateSuit()"
                variant="success"
                class="mr-3"
            >
                Draw Cards
            </b-button>
            <b-button
                v-else
                @click="resetGame()"
                variant="success"
                class="mr-3"
            >
                Reset Game
            </b-button>

            <RulesModal class="ml-3" />
        </div>

        <b-row>
            <b-col>
                <div
                    v-for="(horse, id) in horses"
                    :key=id
                    class="mb-2"
                >
                    <img
                        v-if="horse.position === 0"
                        height="100%"
                        width="100%"
                        :src=horse.card 
                    />
                    <div
                        v-else
                        height="100%"
                        width="100%"
                        class="fakeCard"
                    />
                </div>
            </b-col>
            <b-col>
                <div
                    v-for="(horse, id) in horses"
                    :key=id
                    class="mb-2"
                >
                    <img
                        v-if="horse.position === 1"
                        height="100%"
                        width="100%"
                        :src=horse.card 
                    />
                    <div
                        v-else
                        height="100%"
                        width="100%"
                        class="fakeCard"
                    />
                </div>
            </b-col>
            <b-col>
                <div
                    v-for="(horse, id) in horses"
                    :key=id
                    class="mb-2"
                >
                    <img
                        v-if="horse.position === 2"
                        height="100%"
                        width="100%"
                        :src=horse.card 
                    />
                    <div
                        v-else
                        height="100%"
                        width="100%"
                        class="fakeCard"
                    />
                </div>
            </b-col>
            <b-col>
                <div
                    v-for="(horse, id) in horses"
                    :key=id
                    class="mb-2"
                >
                    <img
                        v-if="horse.position === 3"
                        height="100%"
                        width="100%"
                        :src=horse.card 
                    />
                    <div
                        v-else
                        height="100%"
                        width="100%"
                        class="fakeCard"
                    />
                </div>
            </b-col>
            <b-col>
                <div
                    v-for="(horse, id) in horses"
                    :key=id
                    class="mb-2"
                >
                    <img
                        v-if="horse.position === 4"
                        height="100%"
                        width="100%"
                        :src=horse.card 
                    />
                    <div
                        v-else
                        height="100%"
                        width="100%"
                        class="fakeCard"
                    />
                </div>
            </b-col>
            <b-col>
                <div
                    v-for="(horse, id) in horses"
                    :key=id
                    class="mb-2"
                >
                    <img
                        v-if="horse.position === 5"
                        height="100%"
                        width="100%"
                        :src=horse.card 
                    />
                    <div
                        v-else
                        height="100%"
                        width="100%"
                        class="fakeCard"
                    />
                </div>
            </b-col>
            <b-col>
                <div
                    v-for="(horse, id) in horses"
                    :key=id
                    class="mb-2"
                >
                    <img
                        v-if="horse.position === 6"
                        height="100%"
                        width="100%"
                        :src=horse.card 
                    />
                    <div
                        v-else
                        height="100%"
                        width="100%"
                        class="fakeCard"
                    />
                </div>
            </b-col>
            <b-col>
                <div
                    v-for="(horse, id) in horses"
                    :key=id
                    class="mb-2"
                >
                    <img
                        v-if="horse.position === 7"
                        height="100%"
                        width="100%"
                        :src=horse.card 
                    />
                    <div
                        v-else
                        height="100%"
                        width="100%"
                        class="fakeCard"
                    />
                </div>
            </b-col>
            <b-col>
                <div
                    v-for="(horse, id) in horses"
                    :key=id
                    class="mb-2"
                >
                    <img
                        v-if="horse.position === 8"
                        height="100%"
                        width="100%"
                        :src=horse.card 
                    />
                    <div
                        v-else
                        height="100%"
                        width="100%"
                        class="fakeCard"
                    />
                </div>
            </b-col> 
            <b-col>
                <div
                    v-for="(horse, id) in horses"
                    :key=id
                    class="mb-2"
                >
                    <img
                        v-if="horse.position === 9"
                        height="100%"
                        width="100%"
                        :src=horse.card 
                    />
                    <div
                        v-else
                        height="100%"
                        width="100%"
                        class="fakeCard"
                    />
                </div>
            </b-col>
        </b-row>
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
                    toaster: 'b-toaster-bottom-center'
                })

                this.$confetti.start({
                        particlesPerFramne: .05,
                        defaultDropRate: 20,
                        windSpeedMax: 0,
                        particles: [
                            {
                                type: 'rect',
                                size: 15
                            },
                        ],
                    })
            }
        },
        generateSuit() {
            let suit = this.suits[Math.floor(Math.random() * this.suits.length)]

            this.checkGameOver(suit)     
            this.horses[suit].position++
        },
        resetGame() {
            this.$confetti.stop()
            this.gameOver = false
            for (let suit in this.horses) {
                this.horses[suit].position = 0
            }
        }
    }
}
</script>

<style scoped>
    .fakeCard {
        height: 122px;
        width: 84px;
        background-color: #22303f;
    }
</style>