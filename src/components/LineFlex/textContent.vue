<template>
  <p :style="{color: data.color, 'text-align': data.align}" :class="textClass(data)">{{data.text}}</p>
</template>

<script>
export default {
  props: {
    data: {
      type: Object,
      default: () => {}
    }
  },
  methods: {
    textClass (content) {
      return [
        'w-100pct',
        content.weight ? content.weight : '',
        this.fontSize(content.size),
        content.wrap ? '' : 'nowrap'
      ]
    },
    fontSize (size) {
      return size ? `size-${size}` : 'size-md'
    }
  }
}
</script>

<style scoped>
.bold {
  font-weight: bold;
}

.size-xxs {
  font-size: 11px;
}

.size-xs {
  font-size: 13px;
}

.size-sm {
  font-size: 14px;
}

.size-md {
  font-size: 16px;
}

.size-lg {
  font-size: 19px;
}

.size-xl {
  font-size: 22px;
}

.size-xxl {
  font-size: 29px;
}

.size-3xl {
  font-size: 35px;
}

.size-4xl {
  font-size: 48px;
}

.size-5xl {
  font-size: 74px;
}

.nowrap {
  text-overflow: ellipsis;
  overflow: hidden;
  white-space: nowrap;
}
</style>
