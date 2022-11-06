<template>
  <div>
    <button type="button" @click="$emit('getData')">Test pass data</button>
  </div>
</template>
<script>
export default {
  emits: ["getData"],
};
</script>
<style></style>
