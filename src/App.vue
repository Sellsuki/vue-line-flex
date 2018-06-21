<template>
  <div id="app" class="pd-60px mg-t-100px">
    <LineFlex :data="FlexData" />
  </div>
</template>

<script>
import LineFlex from './components/LineFlex'
import FlexData from './assets/FlexData.json'
export default {
  name: 'app',
  components: {
    LineFlex
  },
  data () {
    return {
      FlexData
    }
  }
}
</script>
