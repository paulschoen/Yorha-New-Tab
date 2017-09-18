<template lang="html">
  <div class='container'>
    <div class='tabs'>
    </div>
    <div class='tabs'>
    </div>
    <div class='tabs'>
    </div>
    <div class='tabs'>
    </div>
    <div class='tabs'>
    </div>
    <div class='tabs'>
    </div>
  </div>
</template>

<script>
</script>

<style lang="css">
.grid .container {
  display: grid;
  grid-template-columns: repeat(6, 1fr);
  grid-gap: 10px;
  grid-auto-rows: minmax(1px, auto);
  height: 35px;
  margin-top: 10px;
}
.tabs{
  background-color: rgba(0, 0, 0, 0.1)
}
</style>
