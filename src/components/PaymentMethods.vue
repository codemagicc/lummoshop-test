<template>
    <div class="icons">
      <div class="icon-inner" v-for="icon in icons" :key="icon.img">
        <img :src="icon.img" :alt="icon.alt" :class="className" />
      </div>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      icons: {
        type: Array,
        required: true,
        validator: (value) => {
          // Validate that each item in the array has 'img' and 'alt' properties
          return value.every((item) => 'img' in item && 'alt' in item)
        }
      },
      className: {
        type: String,
        required: true
      }
    }
  }
  </script>
  