<template>
  <div class="float-left">使用说明</div>
  <button @click="rollBtn">抽取游戏</button>
  <div class="float-right">
    <a id="gameListLink" @click="gameListClick" class="link">{{ gameListText }}</a>
  </div>
  <div class="gameOpt" v-if="gameListShow">
    <a 
      v-for="elem in gameList" 
      @click="this.$emit('ban', elem)" 
      class="link"
      :class="{ banned: bannedList.includes(elem), selected: selectedList.includes(elem) }"
    >{{ elem }}</a>
  </div>
</template>

<script>
export default {
  data() {
    return {
      gameListShow: false,
      gameListText: '▼游戏列表'
    }
  },
  emits: ['roll', 'ban'],
  props: {
    gameList: Array,
    selectedList: Array,
    bannedList: Array
  },
  methods: {
    rollBtn() {
      this.$emit('roll');
    },
    gameListClick() {
      this.gameListShow = !this.gameListShow;
      this.gameListText = this.gameListShow ? '▼游戏列表' : '▲游戏列表';
      console.log(this.gameList)
    }
  }
}
</script>

<style>
.link {
  cursor: pointer;
}

.float-left {
    float: left; 
    width: 100px;
    font-size: small;
    visibility: hidden;
}

.float-right {
    float: right; 
    width: 100px;
    font-size: small;
}

.gameOpt a {
    display: inline-block;
    width: 20%;
    margin: 5px 10px;
}

.gameOpt a:hover {
    color: #999;
    background: #99999933;
}

.selected {
  border: #a47719 solid 2px;
  border-radius: 4px;
}

.banned {
  border: #999 solid 2px;
  border-radius: 4px;
  color: #999;
}
</style>