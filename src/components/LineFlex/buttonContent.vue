<template>
  <button :style="color(data.color)" :class="`flex-button button-${data.style}`">{{data.action.label}}</button>
</template>

<script>
export default {
  props: {
    data: {
      type: Object,
      required: true
    }
  },
  methods: {
    color (color) {
      return color ? `background-color: ${color};` : ''
    }
  }
}
</script>

<style scoped>
.flex-button {
  /* cursor: pointer;
  border-radius: 8px;
  border: 0px;
  text-align: center;
  outline: none;
  width: 100%;
  padding: 12px;
  font-size: 16px;
  color: #4b6393;
  background-color: transparent; */
  display: inherit;
  -webkit-box-align: center;
  align-items: center;
  -webkit-box-pack: center;
  justify-content: center;
  width: 100%;
  height: 52px;
  padding: 0 16px;
  border-radius: 8px;
  font-size: 16px;
  color: #4b6393;
  background-color: transparent;
  outline: none;
  border: 0px;
}
.button-primary {
  background-color: #17c950;
  color: white;
}
.button-secondary {
  background-color: #dddddd;
  color: #181818;
}
</style>
