<template lang="html">
    <div class="container">
      <div class="grid">
        <div class="tab-header">
          <div class="large-border">
            <div class="small-border">
              <ToolBar></ToolBar>
            </div>
          </div>
        </div>
        <div class="repeat-border">
        </div>
        <div class="head1">
          <h1>{{name}}</h1>
        </div>
        <div class="head2">
          <div class="clock-container">
            <Clock displaySeconds=true></Clock>
          </div>
        </div>
        <div class="col1">
          <div class="selection">
            <div style="padding-top: 4em">
              <div class="large-border">
                <div class="small-border">
                  <div class="bookmark-wrapper ">
                    <ListBookmarks></ListBookmarks>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
        <div class="col2">
          <div class="selection">
            <NotePad></NotePad>
          </div>
        </div>
      </div>
      <div class="modals">
      </div>
    </div>
</template>

<script>
import NotePad from './notepad.vue';
import ListBookmarks from './list-bookmarks.vue';
import Modal from './modal.vue';
import Clock from 'vue-digital-clock';
import ToolBar from './tool-bar.vue';

export default {
  data() {
    return {
      name: 'New Tab',
      square: '&#9632'
    }
  },
  components: {
    ListBookmarks: ListBookmarks,
    NotePad: NotePad,
    Clock: Clock,
    Modal: Modal,
    ToolBar: ToolBar
  }
}
</script>

<style lang="css">
  figure {
    margin-left: 2em;
    height: 600px;
  }
  .clock-container {
    text-align: right;
  }
  .clock {
    font-family: helvetica, sans-serif;
    font-weight: 200;
    text-transform: uppercase;
    letter-spacing: 0.5rem;
    text-shadow: 0.3rem 0.3rem 0 #bab5a1;
    display: block;
    font-size: 4em;
    -webkit-margin-before: 0.67em;
    -webkit-margin-after: 0.67em;
    -webkit-margin-start: 0px;
    -webkit-margin-end: 0px;
  }
</style>
