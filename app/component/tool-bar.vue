<template lang="html">
  <div class='container'>
    <div v-if="tabs" v-for="tab in tabs">
      <button style="margin-top: 0px;" type="button" class='tabs'  @click="$event.target.classList.toggle('active')">
        <p class='tabstext'>{{tab.color}}</p>
      </button>
    </div>
  </div>
</template>

<script>
var tabs = [{color:'red'},{color:'orange'},{color:'yellow'},{color:'green'},{color:'blue'},{color:'indigo'}]

export default {
  data() {
    return {
      tabs
    }
  },
}
</script>

<style lang="css">
.grid .container {
  display: grid;
  grid-template-columns: repeat(6, 1fr);
  grid-gap: 15px;
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
</style>
