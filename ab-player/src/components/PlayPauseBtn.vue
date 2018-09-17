<!-- adapted from https://css-tricks.com/making-pure-css-playpause-button/ -->

<template>

 <div class="play-pause-btn" v-bind:class="{ pause: isPlaying }" @click="onClick"></div>

</template>

<script>

export default {
  name: 'PlayPauseBtn',
  props: {
    msg: String
  },
  data: function(){
    return {
      isPlaying: false
    }
  },
  created: function() {
    
  },
  methods: {
    togglePlayPause: function() {
      if (!this.isPlaying) {
        this.isPlaying = true;
        this.$emit('playstate-change', 'play');
      } else {
        this.isPlaying = false;
        this.$emit('playstate-change', 'pause');
      }
    },
    onClick: function() {
      this.togglePlayPause();
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

.play-pause-btn {
  border: 0;
  background: transparent;
  box-sizing: border-box;
  width: 0;
  height: 37px;
  border-color: transparent transparent transparent #34A7C1;
  transition: 100ms all ease;
  cursor: pointer;
  border-style: solid;
  border-width: 18.5px 0 18.5px 30px;
  display: inline-block;
  margin-left: 20px;
}
.play-pause-btn.pause {
  border-style: double;
  border-width: 0px 0 0px 30px;
}
.play-pause-btn:hover {
  border-color: transparent transparent transparent #84def3;
}

</style>
