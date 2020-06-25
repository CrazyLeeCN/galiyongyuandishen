<template>
  <div>
    <div class="label">{{ msg.label }}</div>
    <div class="value">{{ msg.value }}</div>
    <div style="clear:both" />
  </div>
</template>

<script>
export default {
  props: ['msg']
}
</script>
<style scoped>
.label {
  width: 200px;
  float: left;
}
.value {
  float: left;
}
</style>
