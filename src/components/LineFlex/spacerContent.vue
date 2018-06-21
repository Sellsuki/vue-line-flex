<template>
  <div :class="`spacer ${size(data.size)}` "></div>
</template>

<script>
export default {
  props: {
    data: {
      Type: Object,
      required: true
    }
  },
  methods: {
    size (size) {
      return size ? `spacer-${size}` : 'spacer-md'
    }
  }
}
</script>

<style scoped>

/* xs, sm, md, lg, xl,xxl */
.spacer-xs {
  height: 1px;
}
.spacer-sm {
  height: 2px;
}
.spacer-md {
  height: 5px;
}
.spacer-lg {
  height: 10px;
}
.spacer-xl {
  height: 14px;
}
.spacer-xxl {
  height: 20px;
}
.spacer::before {
  content: '';
}
</style>
