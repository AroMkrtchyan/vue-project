<template>
  <div class="window-wrapper">
    <form class="window" @submit.prevent>
      <h1>Card Title</h1>
      <input type="text" name="title" placeholder="card title" required
             v-model="cardData.cardTitle" >
      <h3>Card Description</h3>
      <textarea cols="50" rows="10" name="description" required
                placeholder="card description"
                v-model="cardData.cardDescription"></textarea>
      <h3>Image</h3>
      <input type="file" @change="handleImage" accept="image/*">
      <h5>Date</h5>
      <input type="date" v-model="cardData.cardDate" required>
      <CustomButton text="Create New Card" @buttonClick="formSubmit"/>
      <span class="close-button" @click="formCloser">X</span>
    </form>

  </div>
</template>

<script>
import CustomButton from "./CustomButton";
export default {
  data(){
    return {
      // cardTitle:'',
      // cardDescription:'',
      // cardDate: '',
      // image: '',
    }
  },
  props: {
    data: {
      type: Array,
      required: false,
    },
    cardData: {
      type: Object
    },
    editCard: {
      type: Function
    }
  },
  components: {CustomButton},
  methods: {
    formCloser() {
      this.$emit('formCloser')
    },
    formSubmit() {
      this.$emit('formSubmit')
      console.log(this.cardData)
    },
    handleImage(e){
      this.$emit('handleImage', e)
    },
  }
}
</script>

<style scoped>
.window-wrapper {
  position: absolute;
  top: 0;
  left: 0;
  bottom: 0;
  right: 0;
  display: flex;justify-content: center;
  align-items: center;
  background: rgba(125, 193, 218, 0.44);
}
.window {
  position: relative;
  display: flex;
  flex-direction: column;
  padding: 50px;
  background: rgba(125, 193, 218, 0.80);
  border-radius: 15px;
}
.window > input {
  border-radius: 5px;
  height: 30px;
  outline: none;
  padding: 5px;
  font-size: 18px;
}
h1, h3, h5 {
  margin-top: 25px;
}
.window  button {
  margin-top: 25px;
  min-height: 40px;
  font-size: 20px;
}
.window > textarea {
  outline: none;
  padding: 5px;
}
.close-button {
  position: absolute;
  right: 20px;
  top: 20px;
  font-size: 22px;
  font-weight: bold;
  cursor: pointer;
  background: #ccc;
  width: 35px;
  height: 35px;
  border-radius: 50%;
  display: flex;
  justify-content: center;
  align-items: center;
}

</style>
