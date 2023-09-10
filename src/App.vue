<script>
export default {
  data() {
    return {
      randomNum: 0,
      inputedValue: null,
      isCorrect: undefined,
    };
  },
  methods: {
    onClick() {
      if (+this.randomNum === +this.inputedValue) {
        this.isCorrect = true;
      } else {
        this.isCorrect = false;
        this.inputedValue = null;
      }
      this.generateValue();
    },
    generateValue() {
      const min = 1;
      const max = 10;
      const randomNumber = Math.floor(Math.random() * (max - min + 1)) + min;
      this.randomNum = randomNumber;
    },
  },
  mounted() {
    this.generateValue();
  },
};
</script>

<template>
  <main>
    <div id="container">
      <div class="random-gen">
        <h2>Guess a number between 0 - 9</h2>

        <input
          type="number"
          name="input"
          id="random-nuber"
          v-model="inputedValue"
        />
        <button @click="onClick">Check</button>

        <p v-show="isCorrect" class="correct">Correct !!</p>
        <p v-show="isCorrect === false" class="wrong">
          Wrong! Answer is {{ randomNum }}
        </p>
      </div>
    </div>
  </main>
</template>

<style>
main {
  display: flex;
  flex-direction: column;
  width: 100vw;
  height: 100vh;
  overflow: hidden;
  align-items: center;
  justify-content: center;
}
#container {
  padding: 20px;
  border: 2px solid #333;
  border-radius: 20px;
}

.random-gen input {
  width: 100%;
  height: 30px;
  border: 1px solid #f4f4f4;
  margin-top: 20px;
  background: #fff;
  color: #222;
  padding-left: 10px;
}
</style>
