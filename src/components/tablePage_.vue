/**
	author : sailing
	date : 2016-10-24
	fun: table 分页
***/

<style lang="less">
	.vx-tabelPage{
      height:35px;
      position:relative;
      text-align:center;
      padding-left:10px;
      padding-right:10px;
      color:#fff;
      width:100%;
     
      line-height:30px;
      margin-top:10px;
      display:inline-block;
      .ulPage{
        text-align:left;
        .itemPage{
          width:30px;
          margin-left:5px;
          background:#00d1b2;
          text-align:center;
          display:inline-block
        }
      }
      
	}
</style>

<template>
	<div class="vx-tabelPage">
	  <ul class="ulPage">
      <li class="itemPage" v-show="currentPage > 10"  style="width:100px" @click="prePage()">上一页</li>
      <li class="itemPage" v-show="currentPage > 10"  style="border:0">...</li>
      <li class="itemPage" v-bind:class="{current:}" @click="currentPage($index)" v-for="(item , index) in pageLen">
        {{item + currentPage}}
      </li>
      <li class="itemPage" style="border:0">...</li>
      <li class="itemPage" style="width:100px" @click="nextPage()">下一页</li>
    </ul>
	</div>
</template>

<script>
export default {
  data () {
    return {
      pageLen: 10,
      pageStart: 5,
      currentPage: 1,
      pageEnd: this.pageStart + 10
    }
  },
  methods: {
    clickBnt (e) {
      this.$parent.clickBnt(e, this.id)
    },
    prePage () {
      this.$parent.prePage()
    },
    nextPage () {
      this.$parent.nextPage
    }
  },
  props: {
    bg: String
  }
}
</script>