<template>
  <span :class="'item ' + ((field.value === 1 && preview) ? 'item-active' : '')"></span>

</template>

<script>
export default {
  name: "BoardItem",
  props: {
    field: {
      type: Object,
      required: true,
    },
    preview: {
      type: Boolean,
      required: false,
      default: false,
    }
  },

}
</script>

<style scoped>
.item {
position: relative;
  width: 50px;
  height: 50px;
  background: #ccc;
  display: inline-block;
  margin: 5px;
  cursor: pointer;
  transition: .4s;
  transform-style: preserve-3d;
}

.item-active {
  background: blue;
  transform: rotateX(180deg);
}
</style>