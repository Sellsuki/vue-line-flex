<template>
  <div id="LineFlex" class="T1 w-280px bd-w-1px bd-st-solid bd-bg-cl-white bd-cl-grey-light">
    <boxContent class="pd-20px" v-if="flexData.header" id="header" :data="flexData.header" />
    <imageContent v-if="flexData.hero" id="hero" :data="flexData.hero" />
    <boxContent class="pd-20px" v-if="flexData.body" id="body" :data="flexData.body" />
    <boxContent class="pd-10px" v-if="flexData.footer" id="footer" :data="flexData.footer" />
  </div>
</template>

<script>
import boxContent from './boxContent'
import imageContent from './imageContent'
export default {
  name: 'LineFlex',
  props: {
    data: {
      type: Object,
      required: true
    }
  },
  components: {
    boxContent,
    imageContent
  },
  computed: {
    flexData () {
      const {header, hero, body, footer} = this.data.contents
      let data = {header, hero, body, footer}
      Object.keys(data).forEach(key => {
        if (!data[key]) {
          delete data[key]
        }
      })
      return data
    }
  }
}
</script>

<style>
@import url('./style.css');
.T1 {
  border-radius: 17px;
  overflow: hidden;
  background-color: #ffffff;
  display: flex;
  -webkit-box-orient: vertical;
  -webkit-box-direction: normal;
  flex-direction: column;
}
</style>
