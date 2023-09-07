<script>
export default {
  data() {
    return {
      scoreone: 0,
      scoretwo:0,
      playing: false,
      playerChoice: "",
      computerChoice: "",
      result: "",
      gameOver: false,
      heartchoice:"https://static.thenounproject.com/png/2336169-200.png"
    };
  },
  methods: {
    playGame() {
      const choices = ["https://static.thenounproject.com/png/477918-200.png",
       "https://static.thenounproject.com/png/477922-200.png",
        "https://static.thenounproject.com/png/88666-200.png",
        "https://static.thenounproject.com/png/2336169-200.png"];
      this.playerChoice = choices[Math.floor(Math.random() * choices.length)];
      this.computerChoice = choices[Math.floor(Math.random() * choices.length)];
      this.calculateResult();
      this.playing = true;
    },
    calculateResult() {
      if (this.playerChoice === this.computerChoice) {
        this.result = "เสมอ";
      }else if(this.playerChoice === "https://static.thenounproject.com/png/2336169-200.png"){
        this.result = "ผู้เล่น 1 ชนะ";
        this.scoreone += 1;
      }
      else if(this.computerChoice === "https://static.thenounproject.com/png/2336169-200.png"){
        this.result = "ผู้เล่น 2 ชนะ";
        this.scoretwo += 1;
      }
      
      else if (
        (this.playerChoice === "https://static.thenounproject.com/png/477918-200.png" && this.computerChoice === "https://static.thenounproject.com/png/88666-200.pngg") ||
        (this.playerChoice === "https://static.thenounproject.com/png/477922-200.png" && this.computerChoice === "https://static.thenounproject.com/png/477918-200.png") ||
        (this.playerChoice === "https://static.thenounproject.com/png/88666-200.png" && this.computerChoice === "https://static.thenounproject.com/png/477922-200.png")
      ) {
        this.result = "ผู้เล่น 1 ชนะ";
        this.scoreone += 1;
        this.scoretwo += 0;
      } else {
        this.result = "ผู้เล่น 2 ชนะ";
        this.scoreone += 0;
        this.scoretwo += 1;
      }
    },
    resetGame() {
      this.playing = false;
      this.playerChoice = "";
      this.computerChoice = "";
      this.result = "";
      this.gameOver = false;
      this.scoreone = 0;
      this.scoretwo = 0;
    },
  },
};
</script>
<template>
    <h1>เป่า..ยิ๊ง..ฉุบ!!!!</h1>
  <div v-if="playing" class="row">
  <div class="col-sm-6">
    <div class="card">
      <div class="card-body">
        <h1 class="card-title">ผู้เล่น 1</h1>
        <h2 ><img :src="playerChoice" alt="Choice1"></h2>
        <p>คะแนนผู้เล่น1 : {{ scoreone }}</p>
      </div>
    </div>
  </div>
  <div class="col-sm-6">
    <div class="card">
      <div class="card-body">
        <h1 class="card-title">ผู้เล่น 2</h1>
        <h2> <img :src="computerChoice" alt="Choice2"> </h2>
        <p>คะแนนผู้เล่น2 : {{ scoretwo }}</p>
      </div>
    </div>
  </div>
</div>
<div>
  <br>
<div class="row">
    <div class="col"><button @click="playGame" :disabled="gameOver">เริ่มเกม</button></div>
    <div class="col"><button @click="resetGame">เริ่มใหม่</button></div>
  </div>
</div>
<div>
<h3 v-if="playing">ผล: {{ result }}</h3>
</div>
</template>

<style scoped>
.read-the-docs {
  color: #888;
}
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
</style>
