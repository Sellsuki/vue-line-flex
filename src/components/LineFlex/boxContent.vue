<template>
  <div :class="['MdBx', layout(data.layout), margin(data.margin, '', data.layout, 'box')]">
    <div :key="index" v-for="(content, index) in data.contents" :class="boxClass(content, data, index)">
      <boxContent v-if="content.type === 'box'" :data="content" />
      <textContent v-if="content.type === 'text'" :data="content" />
      <imageContent v-else-if="content.type === 'image'" :data="content" />
      <buttonContent v-else-if="content.type === 'button'" :data="content" />
      <spacerContent v-else-if="content.type === 'spacer'" :data="content" />
    </div>
  </div>
</template>

<script>
import boxContent from './boxContent'
import textContent from './textContent'
import imageContent from './imageContent'
import buttonContent from './buttonContent'
import spacerContent from './spacerContent'
export default {
  name: 'boxContent',
  props: {
    data: {
      type: Object
    }
  },
  components: {
    boxContent,
    textContent,
    imageContent,
    buttonContent,
    spacerContent
  },
  methods: {
    jsUcfirst (string) {
      return string.charAt(0).toUpperCase() + string.slice(1)
    },
    boxClass (content, data, index) {
      if (content.type === 'separator') {
        return [
          'separator',
          this.separator(data.layout),
          index !== 0 ? this.margin(content.margin, 'none') : ''
        ]
      } else if (content.type === 'filler') {
        return ['box-filler']
      } else if (content.type === 'text') {
        return [
          'MdTxt',
          this.margin(content.margin)
        ]
      } else if (content.type === 'button') {
        return [
          'dp-flex',
          index !== 0 ? this.margin(content.margin) : ''
        ]
      } else if (content.type === 'image') {
        return [
          'dp-flex',
          this.width(content.type),
          this.margin(content.margin, 'md'),
          this.height(content.type),
          this.gravity(content),
          this.flex(content.flex, data.layout)
        ]
      }
    },
    margin (margin) {
      if (margin) {
        return `ExT${this.jsUcfirst(margin)}`
      }
      return ''
    },
    height (type) {
      return type === 'text' ? 'h-100pct' : ''
    },
    width (type) {
      return type !== 'separator' ? 'w-100pct' : ''
    },
    textAlign (align) {
      if (align === 'end') {
        return 'ExAlgE'
      } else if (align === 'center') {
        return 'ExAlgC'
      }
      return ''
    },
    gravity (content) {
      if (content.gravity) {
        return `gravity-${content.gravity}`
      }
      return ''
    },
    layout (layout) {
      return layout === 'vertical' ? 'vr' : 'hr'
    },
    flex (size, layout) {
      if (!size) {
        return layout === 'vertical' ? 'flex-0' : 'flex-1'
      }
      return `flex-${size}`
    },
    separator (layout) {
      return `separator-${layout}`
    }
  }
}
</script>

<style scoped>
.boxFlex {
  display: flex;
  width: auto;
  min-width: 0;
  max-width: 100%;
  overflow: hidden;
}
.gravity-top {
  align-items: flex-start;
}
.gravity-center {
  align-items: center;
}
.gravity-bottom {
  align-items: flex-end;
}
.flex-0 {
  flex: none;
}
.flex-1 {
  flex: 1 1 auto;
}
.flex-2 {
  flex: 3 3 auto;
}
.flex-3 {
  flex: 2 2 auto;
}
.separator-vertical {
  border-top: 1px solid #dadada;
  width: 100%;
}

.separator-horizontal {
  border-left: 1px solid #dadada;
  height: 100%;
  width: 1px;
}

.separator::before {
  content: '';
}
.box-filler {
  display: flex;
  flex: 1 1 auto;
  margin: 0;
  width: 100%;
}
</style>
