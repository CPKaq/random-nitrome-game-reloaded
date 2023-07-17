<script>
// import HelloWorld from './components/HelloWorld.vue'
// import TheWelcome from './components/TheWelcome.vue'
import HeaderTitle from './components/Head.vue'
import OptionBox from './components/Option.vue'
import ResultBox from './components/Result.vue'
import ClearBox from './components/Clear.vue'

import gameList from './components/games.js'

export default {
  components: {
    HeaderTitle,
    OptionBox,
    ResultBox,
    ClearBox
},
  data() {
    return {
      nitromeGameList: [],
      candidateList: [],
      selectedList: [],
      bannedList: []
    }
  },
  methods: {
    async loadList() {
      this.nitromeGameList = gameList;
      this.candidateList = gameList.slice();
    },
    addToList(elem) {
      this.selectedList.push(elem);
      // this.candidateList.splice(this.candidateList.indexOf(elem), 1)
      console.log(this.selectedList.join())
      window.scrollBy(0, document.documentElement.clientHeight);
    },
    BanFromList(elem) {
      if(this.bannedList.includes(elem)) {
        this.bannedList.splice(this.bannedList.indexOf(elem), 1)
      } else {
        this.bannedList.push(elem);
      }
      // this.candidateList.splice(this.candidateList.indexOf(elem), 1)
      console.log(this.bannedList.join())
    },
    clearList() {
      this.selectedList.length = 0;
    },
    randomElem() {
      this.candidateList = this.nitromeGameList.filter(
        elem => !this.selectedList.includes(elem) && !this.bannedList.includes(elem))
      length = this.candidateList.length;
      return this.candidateList[Math.floor(Math.random()*length)];
    }
  },
  mounted() {
    this.loadList();
    console.log(this.candidateList);
  },
}
</script>

<template>
  <header class="head">
    <!-- <img alt="Vue logo" class="logo" src="./assets/logo.svg" width="125" height="125" /> -->
    <header-title />
  </header>

  <section>
    <option-box @roll="() => addToList(randomElem())" 
      @ban="(banned) => BanFromList(banned)"
      :gameList="nitromeGameList" 
      :selectedList="selectedList"
      :bannedList="bannedList">
    </option-box>
  </section>

  <main class="result">
    <result-box :gameList="selectedList" />
  </main>

  <section v-if="selectedList.length" class="clear">
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
