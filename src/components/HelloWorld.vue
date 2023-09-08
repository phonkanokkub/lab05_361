<template>
  <div>
    <div class="gameplayer">
      <div>
        <h2>ผู้เล่น 1</h2>
        <div>
          <button @click="selectChoice('ค้อน')">ค้อน</button>
          <button @click="selectChoice('กระดาษ')">กระดาษ</button>
          <button @click="selectChoice('กรรไกร')">กรรไกร</button>
        </div>
        <div>
          {{ person1 }}
        </div>
        <div>
          {{ Result1 }}
        </div>
        <div>
          <img v-if="person1 === 'ค้อน'" src="./one.png" alt="ค้อน" />
          <img v-if="person1 === 'กระดาษ'" src="./two.png" alt="กระดาษ" />
          <img v-if="person1 === 'กรรไกร'" src="./three.png" alt="กรรไกร" />
        </div>
      </div>

      <div>
        <h2>ผู้เล่น 2</h2>
        <div>
          <img v-if="person2 === 'ค้อน'" src="./one.png" alt="ค้อน" />
          <img v-if="person2 === 'กระดาษ'" src="./two.png" alt="กระดาษ" />
          <img v-if="person2 === 'กรรไกร'" src="./three.png" alt="กรรไกร" />
        </div>
        <div>
          {{ person2 }}
        </div>
        <div>
          {{ Result2 }}
        </div>
      </div>
    </div>

    <div>
      <button @click="playRound" class="start-button">เป่ายิ้งงงงงฉุบ!</button>
      <button @click="resetGame" class="reset-button">Reset</button>
    </div>

    <div class="score-game">
      <h3 class="score">คะแนน {{ Score1 }} : {{ Score2 }}</h3>
    </div>
  </div>
</template>


<script>
import { ref } from 'vue';

export default {
  data() {
    return {
      Score1: 0,
      Score2: 0,
      Result1: '',
      Result2: '',
      person1: '',
      person2: '',
      choices: ['ค้อน', 'กระดาษ', 'กรรไกร'],
    };
  },
  methods: {
    selectChoice(choice) {
      this.person1 = choice;
    },
    playRound() {
      const player1Index = this.choices.indexOf(this.person1);
      const player2Index = Math.floor(Math.random() * this.choices.length);

      const person1 = this.person1;
      const person2 = this.choices[player2Index];

      if (person1 === person2) {
        this.Result1 = 'เสมอ';
        this.Result2 = 'เสมอ';
      } else if (
        (person1 === 'ค้อน' && person2 === 'กรรไกร') ||
        (person1 === 'กระดาษ' && person2 === 'ค้อน') ||
        (person1 === 'กรรไกร' && person2 === 'กระดาษ')
      ) {
        this.Result1 = 'ชนะ';
        this.Result2 = 'แพ้';
        this.Score1++;
      } else {
        this.Result1 = 'แพ้';
        this.Result2 = 'ชนะ';
        this.Score2++;
      }
      this.person2 = person2;
    },
    resetGame() {
      this.Score1 = 0;
      this.Score2 = 0;
      this.Result1 = '';
      this.Result2 = '';
      this.person1 = '';
      this.person2 = '';
    },
  },
};
</script>