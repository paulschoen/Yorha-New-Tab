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
          <!-- <div class="selection">
            <div style="padding-top: 4em">
              <div class="large-border">
                <div class="small-border">
                  <figure class="top-sites-visited-figure">
                    <figcaption>Top Sites Visited</figcaption>
                      <hr style="margin: 0; width: 98%;">
                      <div class="bookmark-wrapper list-panel">
                        <TopSites></TopSites>
                      </div>
                      <hr style="margin: 0; width: 98%;">
                  </figure>
                </div>
              </div>
            </div>
          </div> -->
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
import TopSites from './top-sites.vue';
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
    TopSites: TopSites,
    Clock: Clock,
    Modal: Modal,
    ToolBar: ToolBar
  }
}
</script>

<style lang="css">
<<<<<<< HEAD
  figure {
    margin-left: 2em;
    height: 600px;
  }
  h1 {
    -webkit-margin-before: 0;
  }
=======
>>>>>>> master
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
    -webkit-margin-before: 0;
    -webkit-margin-after: 0.67em;
    -webkit-margin-start: 0px;
    -webkit-margin-end: 0px;
  }
  .extend-panel {
    background-color: #dcd8c0;
    padding: 1em;
  }
  .list-panel .top-sites-panel {
    padding: 0.5em 0;
  }
  .list-panel .custom-button {
    width: 95% !important;
  }
  .list-panel button {
    margin-left: 0;  }
  .list-panel a {
    margin-left: 0;
    padding-left: 0;
  }
  .list-panel button:hover {
    background-color: #454138;
  }
  /*.list-panel {
    background-color: rgb(220, 216, 192);
    padding: 0.5em;
    margin-left: 3em;
  }
  .list-panel .top-sites-panel {
    padding: 0.5em 0;
  }
  .list-panel .custom-button {
    width: 100%;
  }
  .list-panel button {
    margin-left: 0;  }
  .list-panel a {
    margin-left: 0;
    padding-left: 0;
  }
  .list-panel button:hover {
    background-color: #454138;
  }*/
</style>
