<template>
  <div class="cardContainer">
    <img :src="imageLink"
         alt="image" class="cardImg">
    <p class="title">
      {{ title.toUpperCase() }}
    </p>
    <p class="description">
      {{description}}
    </p>
    <div class="cardFooter">
      <div class="date">
        {{date}}
      </div>
      <div class="buttonsWrapper">
        <CustomButton :text="'edit'" @buttonClick="editCard"/>
        <CustomButton :text="'delete'" :color="'#8f0707'" @buttonClick="deleteCard"/>
      </div>
    </div>
  </div>

</template>

<script>
import CustomButton from "./CustomButton";
export default {
  props: {
    title: {
      type: String,
      required: true,
    },
    description: {
      type: String,
      required: true
    },
    imageLink: {
      type: String,
      required: true,
    },
    date: {
      type: String,
      required: true,
    },
    itemId: {
      type: Number,
      required: true,
    }
  },
  methods: {
    emitFunc(val) {
      console.log('edit', val)
      // this.$emit('listenEvent', this.itemId)
    },
    editCard() {
      this.$emit('editCard', this.itemId)
    },
    deleteCard() {
      this.$emit('deleteCard', this.itemId)
    }

  },

  components: {CustomButton}

}
</script>

<style scoped>
.cardContainer{
  background: #e5e5e5;
  width: 200px;
  border-radius: 10px;
  padding: 10px;
  box-shadow: 5px 6px 15px 5px rgba(0,0,0,0.55);
  min-height: 300px;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  margin-bottom: 20px;
}
.cardImg {
  width: 100%;
  height: 130px;
  margin-bottom: 15px;
  box-shadow: 0 0 8px 1px rgba(0,0,0,0.89);
}
.title {
  margin-bottom: 15px;
  border-top: 1px solid #ccc;
  padding-top: 5px;
  text-align: center;
  font-weight: bold;
}
.description {
  margin-bottom: 15px;
  border-top: 1px solid #ccc;
  padding-top: 5px;
}
.cardFooter {
  display: flex;
  justify-content: space-between;
  border-top: 1px solid #ccc;
  padding-top: 5px;
}
.buttonsWrapper > button{
  margin-left: 10px;
}
.date {
  font-size: 12px;
  display: flex;
  align-items: center;
  font-weight: bold;
}

</style>
