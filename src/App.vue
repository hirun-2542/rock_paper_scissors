<script setup>
import { ref } from "vue";

const playerScore = ref(0);
const computerScore = ref(0);
const status = ref(null);

const rockEvent = () => {
    let computed = computerChoice();
    if (computed === "rock") {
        console.log("tie");
        status.value = "TIE";
    } else if (computed === "paper") {
        console.log("lose");
        computerScore.value++;
        status.value = "LOSE";
    } else {
        console.log("win");
        playerScore.value++;
        status.value = "WIN";
    }
    console.log(computed);
};
const paperEvent = () => {
    let computed = computerChoice();
    if (computed === "rock") {
        console.log("win");
        playerScore.value++;
        status.value = "WIN";
    } else if (computed === "paper") {
        console.log("tie");
        status.value = "TIE";
    } else {
        console.log("lose");
        computerScore.value++;
        status.value = "LOSE";
    }
    console.log(computed);
};
const scissorsEvent = () => {
    let computed = computerChoice();
    if (computed === "rock") {
        console.log("lose");
        computerScore.value++;
        status.value = "LOSE";
    } else if (computed === "paper") {
        console.log("win");
        playerScore.value++;
        status.value = "WIN";
    } else {
        console.log("tie");
        status.value = "TIE";
    }
    console.log(computed);
};

const choice = ref(["rock", "paper", "scissors"]);
const computerChoice = () => {
    let random = choice.value[Math.floor(Math.random() * choice.value.length)];
    return random;
};

const reset = () => {
    playerScore.value = 0;
    computerScore.value = 0;
    status.value = null;
};
</script>

<template>
    <header><h1>Rock Paper Scissors</h1></header>
    <div class="game">
        <div class="player-computer">
            <span class="player-text">Player</span>
            <span class="computer-text">Computer</span>
        </div>
        <div class="scores">
            <span class="player-score">{{ playerScore }}</span>
            <span class="text">-</span>
            <span class="computer-score">{{ computerScore }}</span>
        </div>
        <div class="status">
            <span
                class="player-score"
                :style="{
                    color:
                        status === 'WIN'
                            ? 'green'
                            : status === 'LOSE'
                            ? 'red'
                            : 'black',
                }"
                >{{ status }}</span
            >
        </div>
        <div class="images">
            <div class="card">
                <img src="../src/assets/rock.png" alt="" @click="rockEvent" />
                <p class="card-text">Rock</p>
            </div>
            <div class="card">
                <img src="../src/assets/paper.png" alt="" @click="paperEvent" />
                <p class="card-text">Paper</p>
            </div>
            <div class="card">
                <img
                    src="../src/assets/scissors.png"
                    alt=""
                    @click="scissorsEvent"
                />
                <p class="card-text">Scissors</p>
            </div>
        </div>
        <div class="reset">
            <button @click="reset">Reset</button>
        </div>
    </div>
</template>

<style scoped>
*,
*::before,
*::after {
    box-sizing: border-box;
    margin: 0;
    position: relative;
    font-weight: normal;
}

.images {
    margin: 0;
    padding: 0;
    display: flex;
    justify-content: space-around;
}

h1 {
    margin: 50px 0;
    font-size: 3rem;
    text-align: center;
    padding: 0;
}

.card-text {
    font-size: 1.5rem;
    text-align: center;
    padding: 0;
    font-weight: bold;
}
.player-computer {
    display: flex;
    align-items: center;
    text-align: center;
    justify-content: space-around;
    width: 50%;
    margin: auto;
    font-size: 2rem;
    height: 100%;
}
.scores {
    display: flex;
    align-items: center;
    text-align: center;
    justify-content: space-evenly;
    width: 45%;
    margin: auto;
    font-size: 2rem;
    height: 100%;
    margin-bottom: 30px;
}

.text {
    margin: 0 20px;
}

.player-text,
.computer-text {
    font-size: 1.5rem;
    font-weight: bold;
}

.status {
    display: flex;
    align-items: center;
    text-align: center;
    justify-content: center;
    margin: auto;
}

.status span {
    font-family: "Trebuchet MS", "Lucida Sans Unicode", "Lucida Grande",
        "Lucida Sans", Arial, sans-serif;
    font-weight: bolder;
    font-size: 3rem;
}

.card img:hover {
    cursor: pointer;
    transform: scale(1.1);
    transition: all 0.3s ease;
}

.reset {
    display: flex;
    align-items: center;
    text-align: center;
    justify-content: center;
    margin: 30px auto;
}

.reset button {
    font-size: 2rem;
    padding: 10px 20px;
    cursor: pointer;
    border-radius: 10px;
}

.reset button:hover {
    background-color: darkgrey;
    transition: all 0.3s ease;
}
</style>
