<!-- generated from https://proto.io/freebies/onoff/ -->
<template>
  <div class="onoffswitch">
    <input type="checkbox" name="onoffswitch" class="onoffswitch-checkbox" v-bind:id="this.id">
    <label class="onoffswitch-label" v-bind:for="this.id" @click="onClick">
        <span class="onoffswitch-inner"></span>
        <span class="onoffswitch-switch"></span>
    </label>
  </div>
</template>

<script>

export default {
  name: 'ToggleSwitch',
  data: function() {
    return {
      id: null,
      isOff: false
    }
  },
  created: function() {
    this.id = this._uid
  },
  methods: {
    onClick: function() {
      if (!this.isOff) {
        this.isOff = true;
        this.$emit('playstate-change', 'wet-solo');
      } else {
        this.isOff = false;
        this.$emit('playstate-change', 'dry-solo');
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.onoffswitch {
  position: relative; width: 90px;
  -webkit-user-select:none; -moz-user-select:none; -ms-user-select: none;
  display: inline-block;
  position: relative;
  top: -1.5px;
}
.onoffswitch-checkbox {
  display: none;
}
.onoffswitch-label {
  display: block; overflow: hidden; cursor: pointer;
  border: 2px solid #EBEBEB; border-radius: 20px;
}
.onoffswitch-inner {
  display: block; width: 200%; margin-left: -100%;
  transition: margin 0.3s ease-in 0s;
}
.onoffswitch-inner:before, .onoffswitch-inner:after {
  display: block; float: left; width: 50%; height: 30px; padding: 0; line-height: 30px;
  font-size: 14px; color: white; font-family: Trebuchet, Arial, sans-serif; font-weight: bold;
  box-sizing: border-box;
}
.onoffswitch-inner:before {
  content: "WET";
  padding-right: 28px;
  background-color: #34A7C1; color: #FFFFFF;
}
.onoffswitch-inner:after {
  content: "DRY";
  padding-right: 10px;
  background-color: #EEEEEE; color: #999999;
  text-align: right;
}
.onoffswitch-switch {
  display: block; width: 18px; margin: 6px;
  background: #FFFFFF;
  position: absolute; top: 0; bottom: 0;
  right: 56px;
  border: 2px solid #EBEBEB; border-radius: 20px;
  transition: all 0.3s ease-in 0s; 
}
.onoffswitch-checkbox:checked + .onoffswitch-label .onoffswitch-inner {
  margin-left: 0;
}
.onoffswitch-checkbox:checked + .onoffswitch-label .onoffswitch-switch {
  right: 0px; 
}
</style>
