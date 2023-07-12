<template>
  <div class="float-left">使用说明</div>
  <button @click="rollBtn">抽取游戏</button>
  <div class="float-right">
    <a id="gameListLink">▼游戏列表</a>
  </div>
  <div class="gameOpt"></div>
</template>

<script>
export default {
  // 声明触发的事件
  emits: ['roll'],
  // created() {
  //   this.$emit('roll', 'test')
  // }
  methods: {
    rollBtn() {
      this.$emit('roll', 'test');
    }
  }
}
</script>

<style>
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
    text-decoration: line-through;
}
</style>