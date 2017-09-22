<template lang="html">
  <div class='container'>
    <div v-if="tabs" v-for="tab in tabs">
      <button style="margin-top: 0px;" type="button" class='tabs' v-bind:class="[ tab.active ? 'active' : '']" v-on:click="setActive(tab)">
        <p class='tabstext'>{{tab.name}}</p>
        <img class="black-arrow arrow animated fadeIn" src="/images/arrow.png" alt="arrow">
        <img class="white-arrow animated fadeIn" src="/images/white_arrow.png" alt="white arrow">
      </button>
    </div>
  </div>
</template>

<script>
import VueLocalStorage from 'vue-localstorage';
import Vue from 'vue';
import $ from 'jquery';
import App from './app.vue';

Vue.use(VueLocalStorage)

var tabs = [{
    name: 'Note Pad',
    active: true,
  },
  {
    name: 'Top Visited Sites',
    active: false,
  },
  {
    name: 'tab3',
    active: false,
  },
  // {
  //   name: 'tab4',
  //   active: false,
  // },
  // {
  //   name: 'tab5',
  //   active: false,
  // },
  // {
  //   name: 'tab6',
  //   active: false,
  // }
]


export default {
  mounted() {
    this.tabs.forEach((tab) => {
      if (Vue.localStorage.get('activeTab') === tab.name) {
        tab.active = true;
      } else {
        tab.active = false;
      }
    })
  },
  data() {
    return {
      tabs,
      activeTab: Vue.localStorage.get('activeTab')
    }
  },
  methods: {
<<<<<<< Updated upstream
    setActive: function(selectedTab) {
      var tabs = this.tabs;
      var activeTab = this.activeTab;
      tabs.forEach((tab) => {
        tab.active = false;
      })
      selectedTab.active = true;
      activeTab = selectedTab.name
      this.$parent.setAppActiveTab(activeTab);
=======
      greet: function (event) {
        document.querySelectorAll(".tabs").forEach(function(i){
          i.classList.remove('active')
        })
        document.querySelector("."+event).classList.toggle('active')
      }
>>>>>>> Stashed changes
    }
  }
}
</script>

<style lang="css">
.grid .container {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-gap: 34px;
  height: 35px;
  margin-top: 10px;
}
.tabs{
  background-color: rgba(0, 0, 0, 0.1);
  width: 100%;
  height: 35px;
  display: table;
}
.tabstext{
  font-size: 20px;
  text-transform: uppercase;
  display: table-cell;
  vertical-align: middle;
}
.active{
  background-color: #454138 !important;
  height: 55px;
  color: #dcd8c0 !important;
}
button.active:hover {
  -webkit-box-shadow: none !important;
  box-shadow: none !important;
}
button.active:hover:before {
  border: transparent !important;
}
</style>
