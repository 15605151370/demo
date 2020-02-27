<template>
  <div id="app">
    <div class="header">
      <div class="title" @click="showPicker">
        <span>全部赛事</span>
        <i class="cubeic-select" :class="{flip: toFlip}" ref="select"></i>
      </div>
      <div class="navigator">
        <ul class="nav-list">
          <li v-for="(item, index) in tabList" :key="index"
              @click="switchTab(index)" :class="{active: currentPage === index}">
            {{ item }}
          </li>
        </ul>
        <div class="triangle-up" :class="{left: currentPage === 0, right: currentPage === 2}"></div>
      </div>
    </div>
    <div class="content">
      <cube-slide
        :data="tabList"
        :initialIndex="currentPage"
        :loop="false"
        :autoPlay="false"
        :threshold="0.1"
        @change="slideChange">
        <cube-slide-item v-for="(item, index) in tabList" :key="index">
          <div class="match-list-wrapper">
            <match-list :type="type" :status="index"></match-list>
          </div>
        </cube-slide-item>
        <div slot="dots"></div>
      </cube-slide>
    </div>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld'

export default {
  name: 'app',
  components: {
    HelloWorld
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;

  margin-top: 60px;
}
</style>
