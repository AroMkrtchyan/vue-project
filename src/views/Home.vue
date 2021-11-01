<template>
  <div class="home">
    <div class="search-bar">
      <SearchBar @buttonClick="openWindow"/>
      <Window v-if="window" @openWindow="openWindow"
              @formCloser="openWindow" @formSubmit="formSubmit"/>
    </div>
    <div class="home-content">
      <Card v-for="card in cards"
            :title="card.title" :description="card.description"
            :imageLink="card.imageLink" :date="card.date"
            @listenEvent="func"
      />
    </div>

  </div>
</template>

<script>
import Card from "../components/Card";
import SearchBar from "../components/SearchBar";
import Window from "../components/Window"
export default {
  data() {
    return {
      cards:[
        {title: 'hello title',
         description: 'hello description',
         imageLink: 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTExtoLVhMIfPRj_8d5RQKF2qjwUbuYL2tZTg&usqp=CAU',
         date: '20.15'},
        {title: 'hello title',
          description: 'hello description',
          imageLink: 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTExtoLVhMIfPRj_8d5RQKF2qjwUbuYL2tZTg&usqp=CAU',
          date: '20.15'},
        {title: 'hello title',
          description: 'hello description',
          imageLink: 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTExtoLVhMIfPRj_8d5RQKF2qjwUbuYL2tZTg&usqp=CAU',
          date: '2021-20-15'},
      ],
      window: false,
    }
  },
  methods: {
    func(val) {
      console.log('func')
    },
    openWindow(){
      this.window = !this.window
    },
    formSubmit(title, description, date){
      this.cards.push({
        title,
        description,
        date,
      })
      console.log('submit')
      this.openWindow()
    }
  },
  components: {SearchBar, Card, Window}
}
</script>

<style scoped>
.home {
  padding: 30px;
}
.home-content{
  display: flex;
  flex-wrap: wrap;
  justify-content: space-around;
}
</style>
