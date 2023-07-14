<script>
// import HelloWorld from './components/HelloWorld.vue'
// import TheWelcome from './components/TheWelcome.vue'
import HeaderTitle from './components/Head.vue'
import OptionBox from './components/Option.vue'
import ResultBox from './components/Result.vue'
import ClearBox from './components/Clear.vue'

import nitromeGameList from './components/games.js'

export default {
  components: {
    HeaderTitle,
    OptionBox,
    ResultBox,
    ClearBox
},
  data() {
    return {
      candidateGameList: [],
      msgList: []
    }
  },
  methods: {
    async loadList() {
      this.candidateGameList = nitromeGameList;
    },
    addList(msg) {
      this.msgList.push(msg);
    },
    clearList() {
      this.msgList.length = 0;
    },
    randomElement() {
      length = this.candidateGameList.length;
      return this.candidateGameList[Math.floor(Math.random()*length)];
    }
  },
  mounted() {
    this.loadList();
    console.log(this.candidateGameList);
  },
}
</script>

<template>
  <header class="head">
    <!-- <img alt="Vue logo" class="logo" src="./assets/logo.svg" width="125" height="125" /> -->
    <header-title />
  </header>

  <section class="option">
    <option-box @roll="(msg) => addList(randomElement())">
    </option-box>
  </section>

  <div>
    <p v-for="game in nitromeGameList">{{ game }}</p>
  </div>

  <main class="result">
    <result-box :gameList="msgList" />
  </main>

  <section v-if="msgList.length" class="clear">
    <clear-box @clear="clearList"/>
  </section>
</template>

<style>
@font-face {
font-family: FFF-Neostandard;
src:url('//cpk.moe/random-nitrome-game/FFF-Neostandard.ttf');
}

body {
    text-align: center;
    margin: 0;
    background: #f9ecc3;
}

a {
    text-decoration: none;
    color: #a47719;;
}

.head {
    background: #a47719;
    padding: 20px 0;
}

.head h1 {
    margin: 0;
}

.option {
    padding: 20px 0;
    border-bottom: #967227 solid 1px;
}

.float {
    position: fixed;
    top: 0;
    width: 100%;
    background: #f9ecc3;
    display: none;
}

.result {
    margin: 20px 0 85px 0;
    font-size: 300%;
    font-family: FFF-Neostandard;
}

.result p {
    margin: 10px 0;
}

.clear {
    position: fixed;
    bottom: 0;
    width: 100%;
    padding: 20px 0;
    background: #f9ecc3;
    border-top: #967227 solid 1px;
}
</style>
