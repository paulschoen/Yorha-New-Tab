<template lang="html">
  <div v-bind:class="{ active: showModal }" class="modal">
    <figure>
      <figcaption>
        <div class="header">
          <div class="title">
            {{title}}
          </div>
          <div class="close-button">
            <span v-on:click="showModal ? showModal = false : showModal = true" class="close-btn">X</span>
          </div>
        </div>
      </figcaption>
      <div class="modal-content">
        {{content}}
      </div>
    </figure>
  </div>
</template>

<script>
export default {
  data() {
    return {
      showModal: true,
    }
  },
  props: ['content', 'title', 'showModal']
}
</script>

<style lang="css">
  .modal {
    display: none; /* Hidden by default */
    position: fixed; /* Stay in place */
    z-index: 1; /* Sit on top */
    left: 0;
    top: 0;
    width: 100%; /* Full width */
    height: 100%; /* Full height */
    overflow: auto; /* Enable scroll if needed */
    background-color: rgb(0,0,0); /* Fallback color */
    background-color: rgba(0,0,0,0.4); /* Black w/ opacity */
  }
  .modal > figure {
    margin: 6em 10em;
  }
  .active {
    display: block;
  }
  .header {
    display: inline;
  }
  .title{
    display: inline;
  }
  .close-button{
    text-align: right;
    float: right;
    display: inline;
  }
  .close-btn {
    cursor: pointer;
  }

</style>
