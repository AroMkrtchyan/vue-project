<template>
  <div class="home">
    <div class="search-bar">
      <SearchBar @AddButtonClick="openWindow" @searchButtonClick="searchButtonClick"/>
      <Window v-if="window" @openWindow="openWindow" :data="this.cards" :editCard="editCard"
              @formCloser="openWindow" @formSubmit="formSubmit"/>
    </div>
    <div class="home-content">
      <Card v-for="card in filteredData" :itemId="card.id"
            :title="card.title" :description="card.description"
            :imageLink="card.imageLink" :date="card.date"
            @editCard="editCard" @deleteCard="deleteCard"
      />
      <h1 v-if="filteredData.length === 0" class="message">No Cards</h1>
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
        {id:1,
         title: 'hello title',
         description: 'hello description',
         imageLink: 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTExtoLVhMIfPRj_8d5RQKF2qjwUbuYL2tZTg&usqp=CAU',
         date: '20.15'},
        {id:2,
         title: 'hello title',
         description: 'hello description',
         imageLink: 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTYIX4fdymadei7FiL-19pxFAWPLEJgQlNEww&usqp=CAU',
         date: '20.15'},
        {id:3,
         title: 'hello title',
         description: 'hello description',
         imageLink: 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQUljqj4bvR3hqD9XeBTjEeNubLiwtjlkJS3A&usqp=CAU',
         date: '2021-20-15'},
      ],
      window: false,
      searchInput: ''
    }
  },
  methods: {
    editCard(itemId) {
      this.openWindow()
      console.log(itemId,)
    },
    deleteCard(itemId) {
      this.cards = this.cards.filter(card => card.id !== itemId)
    },
    openWindow(){
      this.window = !this.window
    },
    formSubmit(title, description, date, imageLink){
      this.cards.push({
        id: new Date().getTime(),
        title,
        description,
        date,
        imageLink,
      })
      this.openWindow()
    },
    searchButtonClick(searchInput){
      this.searchInput = searchInput
    }
  },
  computed:{
    filteredData(){
      if (this.searchInput) {
        return this.cards.filter(card => {
          return card.title.indexOf(this.searchInput) !== -1 || card.description.indexOf(this.searchInput) !==-1
        })
      } else {
        return this.cards
      }
    },
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
.message {
  font-size: 50px;
  color: #FFF;
  background: #a8a8a8;
  padding: 10px;
  border-radius: 20px;

}
</style>
