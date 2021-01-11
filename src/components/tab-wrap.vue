<template>
  <div class="tab-wrap" ref="tabWrap">
    <ul class="tab-title" id="tabTitle" ref="tabTitle" :style="compWrapStyle" :class="{'fix-table-title': fixState}">
      <li class="title-list" v-for="(item, index) in tabTitleList" :key="index"
          @click="choseTab(item, index)"
          :style="compTitleStyle"
          :class="{'tab-tabActive':tabActive===index}" >
        {{item}}
      </li>
    </ul>
    <div class="tab-wrap-content"><slot></slot></div>
  </div>
</template>

<script>
export default {
  name: "tab-wrap",
  props:{
    tabTitleList:{
      type:Array,
      default:()=>[],
      required:true
    },
    tabTitleHeight:{
      type: Number,
      default:55
    },
    tabTitleBg:{
      type:String,
      default:'#fff'
    },
    tabActiveColor:{
      type:String,
      default:'#07664f'
    },
    tabWrapBg:{
      type:String,
      default:'#fff'
    }
  },
  computed:{
    compTitleStyle(index){
      return {
        height:this.tabTitleHeight+'px',
        lineHeight:this.tabTitleHeight+'px',
        background:this.tabTitleBg,
      }
    },
    compWrapStyle(){
      return {background:this.tabWrapBg}
    }
  },
  data(){
    return {
      tabActive:0,
      tableTitleHeight:0,
      tabHeightList:[],
      tabOffsetTop:[],
      tabState: false,
      fixState: false,
      firstOffsetTop:0,
      clickIndex:null,
      scrollIndex: null,
      isClickTab: false,
      // endX: 0,
    }
  },
  mounted() {
    this.tableTitleHeight = this.$refs['tabTitle'].offsetHeight
    this.concludeHeight()
    this.watchScroll()
    this.firstOffsetTop = this.$refs['tabTitle'].offsetTop
    this.operateHammer()
  },
  methods:{
    // 建通scroll
    watchScroll(){
      const _this = this
      window.addEventListener('scroll',function (){
        let scrollT = 0
        if (document.documentElement && document.documentElement.scrollTop) {
          scrollT = document.documentElement.scrollTop;
        } else if (document.body) {
          scrollT = document.body.scrollTop;
        }
        _this.watchScrollVal(scrollT)
      })
    },
    watchScrollVal(scrollT){
      this.fixState = false
      if(document.documentElement.scrollTop >= this.firstOffsetTop){
        this.fixState = true
      }
      this.tabOffsetTop.forEach((res, index)=>{
        if(scrollT+90>=res && scrollT+90 <this.tabOffsetTop[index+1]){
          if(this.isClickTab) return false
          this.scrollIndex = index
          this.tabActive = index
        }
      })
    },
    concludeHeight(){
      this.$slots.default.forEach(res=>{
        if(res.tag !== undefined){
          this.tabHeightList.push(res.elm.offsetHeight)
          this.tabOffsetTop.push(res.elm.offsetTop)
        }
      })
    },
    //选择
    choseTab(val, index){
      this.tabActive = index
      this.isClickTab = true
      const _this = this
      setTimeout(()=>_this.isClickTab = false, 300)
      this.$slots.default.forEach(res=>{
        if(res.tag !== undefined && res.elm.title === val) {
          let totalSum = 0
          try {
            totalSum = this.tabHeightList.slice(0, index).reduce((a,b)=>a+b)
          } catch (err){
            totalSum = 0
          }
          document.documentElement.scrollTop = totalSum+this.$refs['tabWrap'].offsetTop - 25
          this.clickIndex = index
        }
      })
    },
    operateHammer(){
      // let initX = 0
      // const dragDom = self.$refs['board']
    }
  }
}
</script>

<style scoped >
.fix-table-title{
  position: fixed;
  top: 0;
}
.tab-wrap{
  width: 100%;
  box-sizing: border-box;
}
.tab-wrap-content{
  width: 100%;
  padding-top: 40px;
}
.tab-title{
  width: 100%;
  overflow-x: scroll;
  overflow-y: hidden;
  white-space: nowrap;
  background: #e9e6e6;
}
.tab-title::-webkit-scrollbar {
  width: 0;
  height: 0;
  display: none;
}
.title-list{
  margin: 0 20px;
  font-size: 15px;
  box-sizing: border-box;
  display: inline-block;
}
.title-list:hover{
  cursor: pointer;
}
.tab-tabActive{
  border-bottom: 2px solid #07664f;
}
</style>
