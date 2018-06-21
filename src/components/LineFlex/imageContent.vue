<template>
  <div id="flex-image" :class="`${size(data.size)} ${aspectMode(data.aspectMode)}`">
    <img :src="data.url" alt="">
  </div>
</template>

<script>
export default {
  name: 'flex-image',
  props: {
    data: {
      type: Object,
      required: true
    }
  },
  methods: {
    size (size) {
      return size ? `size-${size}` : 'size-md'
    },
    aspectMode (mode) {
      return mode ? `mode-${mode}` : ''
    }
  }
}
</script>

<style scoped>
/* size (xxs, xs, sm, md, lg, xl, xxl, 3xl, 4xl, 5xl, full)  */
.size-xxs {
  width: 40px;
}
.size-xs {
  width: 60px;
}
.size-sm {
  width: 80px;
}
.size-md {
  width: 100px;
}
.size-lg {
  width: 120px;
}
.size-xl {
  width: 140px;
}
.size-xxl {
  width: 160px;
}
.size-3xl {
  width: 180px;
}
.size-4xl {
  width: 200px;
}
.size-5xl {
  width: 220px;
}
.size-full {
  width: 100%;
}
.mode-cover {
  margin: -5px;
  margin-bottom: 0px;
}
</style>
