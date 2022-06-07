<script>
export default {
  props: {
    integers: Number
  },
  emits: ['remove'],
}
</script>

<template>
  <div class="card-container">
    <p class="delete">
      <span @click="$emit('remove')">X</span>
    </p>

    <div class="integers">
      {{ integers }}
    </div>
  </div>
</template>

<style>
.card-container {
  width:300px;
  height:200px;
  margin: 20px 20px;
  border: 1px solid;
}

.delete {
  text-align: right;
  padding-right: 20px;
  cursor: pointer;
}

.integers {
  text-align: center;
  font-size: 40px;
}
</style>
