<template>
  <div id="LineFlex" class="T1 w-280px bd-w-1px bd-st-solid bd-bg-cl-white bd-cl-grey-light">
    <component :id="key" v-for="(data, key) in flexData" :key="key" :data="data" :class="findPadding(key)" :is="findComponent(key)"></component>
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
  methods: {
    findComponent (key) {
      const compConst = {
        header: 'boxContent',
        hero: 'imageContent',
        body: 'boxContent',
        footer: 'boxContent'
      }
      return compConst[key] ? compConst[key] : ''
    },
    findPadding (key) {
      const pdConst = {
        header: 'pd-20px',
        hero: '',
        body: 'pd-20px',
        footer: 'pd-10px'
      }
      return pdConst[key] ? pdConst[key] : ''
    }
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
