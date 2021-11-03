<template>
  <div class="home">
    <div class="search-bar">
      <SearchBar @AddButtonClick="openWindow" @searchButtonClick="searchButtonClick"/>
      <Window v-if="window" @openWindow="openWindow" :data="this.cards"
              :editCard="editCard" :cardData="this.cardData" @handleImage="handleImage"
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
      cardData: {
        cardTitle:'',
        cardDescription:'',
        cardDate: '',
        imageLink: '',
      },
      cards:[
        {id:1,
         title: 'hello title',
         description: 'hello description',
         imageLink: 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTExtoLVhMIfPRj_8d5RQKF2qjwUbuYL2tZTg&usqp=CAU',
         date: '0011-11-11'},
        {id:2,
         title: 'hello title',
         description: 'hello description',
         imageLink: 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTYIX4fdymadei7FiL-19pxFAWPLEJgQlNEww&usqp=CAU',
         date: '0011-11-11'},
        {id:3,
         title: 'hello title',
         description: 'hello description',
         imageLink: 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQUljqj4bvR3hqD9XeBTjEeNubLiwtjlkJS3A&usqp=CAU',
         date: '0011-11-11'},
      ],
      window: false,
      searchInput: ''
    }
  },
  methods: {
    editCard(itemId) {
      const selectedItem = this.cards.filter(card => card.id === itemId)
      this.cardData.id = selectedItem[0].id
      this.cardData.cardTitle = selectedItem[0].title
      this.cardData.cardDescription = selectedItem[0].description
      this.cardData.cardDate = selectedItem[0].date
      this.cardData.imageLink = selectedItem[0].imageLink
      this.openWindow()
    },
    deleteCard(itemId) {
      this.cards = this.cards.filter(card => card.id !== itemId)
    },
    openWindow(){
      this.window = !this.window
    },
    formSubmit(){
      if(!this.cardData.id){
        this.cards.push({
          id: new Date().getTime(),
          title: this.cardData.cardTitle,
          description: this.cardData.cardDescription,
          date: this.cardData.cardDate,
          imageLink: this.cardData.imageLink,
        })
        this.openWindow()
      }else{
        this.cards.forEach(card => {
          if(card.id === this.cardData.id){
            card.title=this.cardData.cardTitle
            card.description=this.cardData.cardDescription
            card.imageLink=this.cardData.imageLink
            card.date=this.cardData.cardDate
          }
        })
        this.openWindow()
      }
    },
    searchButtonClick(searchInput){
      this.searchInput = searchInput
    },
    handleImage(e){
      const selectedImage = e.target.files[0]
      this.createBase64Image(selectedImage)
    },
    createBase64Image(fileObject) {
      const reader = new FileReader();
      reader.onload = (e) => {
        this.cardData.imageLink = e.target.result
      }
      reader.readAsBinaryString(fileObject)
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
