<template>
  <div class="hello">
    <h1>AB Player component</h1>
    <ToggleSwitch @playstate-change="changePlayState" />
    <PlayPauseBtn @playstate-change="changePlayState"/>
    <div class="time-labels">
      <label class="elapsed">{{elapsedTime}}</label>
      /
      <label class="duration">{{trackDuration}}</label>
    </div>
  </div>
</template>

<script>
import ToggleSwitch from './ToggleSwitch.vue'
import PlayPauseBtn from './PlayPauseBtn.vue'
import {Howl, Howler} from 'howler';

export default {
  name: 'ABPlayer',
  props: {
    msg: String
  },
  components: {
    ToggleSwitch: ToggleSwitch,
    PlayPauseBtn: PlayPauseBtn
  },
  data: function() {
    return {
      trackA: {},
      trackB: {},
      elapsedTime: '0.00'
    }
  },
  methods: {
    renderElapsedTime: function() {
      var that = this;
      setInterval(function(){
        if (typeof that.trackA.seek() === 'number') {
          that.elapsedTime = that.trackA.seek().toFixed(2);
        }        
      }, 100);
    },
    changePlayState: function(event) {
      console.log('time elapsed: ' + this.trackA.duration());
      console.log('play state changed');
      console.log(event);
      if (event === 'play') {
        this.trackA.play();
        this.trackB.play();
      }
      else if (event === 'pause') {
        this.trackA.pause();
        this.trackB.pause();
      }
      else if (event === 'wet-solo') {
        this.trackA.mute(true);
        this.trackB.mute(false);
      }
      else if (event === 'dry-solo') {
        this.trackA.mute(false);
        this.trackB.mute(true);
      }
    }
  },
  computed: {
    trackDuration: function() {
      var duration = this.trackA.duration();
      return duration .toFixed(2); // round to 2 dp
    }
  },
  created: function() {
    // init track A and B
    var trackAFilepath = require('../assets/audio/vocoderdry.mp3');
    var trackBFilepath = require('../assets/audio/vocoderwet.mp3')

    this.trackA = new Howl({
      src: trackAFilepath,
      onend: function() {
        console.log('ended');
        
      }
    });
    this.trackB = new Howl({
      src: trackBFilepath,
      mute: true
    });

    // set timeout for elapsed label
    this.renderElapsedTime();

  
    


    
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
.time-labels {
  position: relative;
  top: -10px;
  display: inline-block;
}
label.elapsed, label.duration {
  text-align: left;
  display: inline-block;
}
label.elapsed {
  width: 56px;
  text-align: right;
}
</style>
