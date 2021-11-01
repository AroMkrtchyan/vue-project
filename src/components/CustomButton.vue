<template>
    <button class="button"  :style="`color: ${color}`" @click="buttonClick">
      {{text}}
    </button>
</template>

<script>
  export default {
    props: {
      text: {
        type: String,
        required:true,
      },
      color: {
        type: String,
        required: false,
        default: '#ffffff'
      }
    },
    methods: {
      buttonClick() {
        this.$emit("buttonClick")
      }
    }
  }
</script>

<style scoped>
.button {
  box-shadow: 0 10px 14px -7px #276873;
  background:linear-gradient(to bottom, #599bb3 5%, #408c99 100%);
  background:#599bb3;
  border-radius:5px;
  cursor:pointer;
  font-size:14px;
  padding:2px 4px;
  text-shadow:0 1px 0 #3d768a;
  min-width: 50px;
}
.button:hover {
  background:linear-gradient(to bottom, #408c99 5%, #599bb3 100%);
  background:#408c99;
}
.button:active {
  position:relative;
  top:1px;
}
</style>
