<template>
  <div id="app">
    <div style="height: 500px"></div>
    <tab-wrap :tabTitleList="tabTitleList">
      <tab title="实现横">
        <div class="tab1">实现横</div>
      </tab>
      <tab title="实现横向">
        <div class="tab2">实现横向</div>
      </tab>
      <tab title="实现横向滑动">
        <div class="tab3">实现横向滑动</div>
      </tab>
      <tab title="实现横">
        <div class="tab1">实现横</div>
      </tab>
      <tab title="实现横向">
        <div class="tab2">实现横向</div>
      </tab>
      <tab title="实现横向滑动">
        <div class="tab3">实现横向滑动</div>
      </tab>
      <tab title="实现横">
        <div class="tab1">实现横</div>
      </tab>
      <tab title="实现横向">
        <div class="tab2">实现横向</div>
      </tab>
      <tab title="实现横向滑动">
        <div class="tab3">实现横向滑动</div>
      </tab>
      <tab title="实现横">
        <div class="tab1">实现横</div>
      </tab>
      <tab title="实现横向">
        <div class="tab2">实现横向</div>
      </tab>
      <tab title="实现横向滑动">
        <div class="tab3">实现横向滑动</div>
      </tab>
      <tab title="实现横">
        <div class="tab1">实现横</div>
      </tab>
      <tab title="实现横向">
        <div class="tab2">实现横向</div>
      </tab>
      <tab title="实现横向滑动">
        <div class="tab3">实现横向滑动</div>
      </tab>
      <tab title="实现横">
        <div class="tab1">实现横</div>
      </tab>
      <tab title="实现横向">
        <div class="tab2">实现横向</div>
      </tab>
      <tab title="实现横向滑动">
        <div class="tab3">实现横向滑动</div>
      </tab>
    </tab-wrap>
  </div>
</template>

<script>
import tabWrap from './components/tab-wrap'
import tab from './components/tab'
export default {
  name: 'app',
  components:{
    tabWrap,
    tab
  },
  data () {
    return {
      tabTitleList:['实现横','实现横向','实现横向滑动','实现横','实现横向','实现横向滑动','实现横','实现横向','实现横向滑动','实现横','实现横向','实现横向滑动','实现横','实现横向','实现横向滑动','实现横','实现横向','实现横向滑动']
    }
  }
}
</script>

<style>
*{
  margin: 0;
  padding: 0;
}
html, body,#app {
  width: 100%;
  height: 100%;
}
ul,li{
  list-style: none;
}
.tab1{
  height: 800px;
}
.tab2{
  height: 700px;
}
.tab3{
  height: 700px;
}
</style>
