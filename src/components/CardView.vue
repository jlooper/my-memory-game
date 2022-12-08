<template>
  <div :class="`view ${viewType}-view`">
    <img :src="imageUrl" :alt="imageAltText" />
  </div>
</template>

<script>
export default {
  props: {
    viewType: {
      type: String,
      required: true,
    },
    imageUrl: {
      type: String,
      default: `/que_icon.svg`,
    },
    imageAltText: {
      type: String,
      default: `hidden card`,
    },
  },
};
</script>