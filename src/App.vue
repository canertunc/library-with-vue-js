<template>
  <appHeader />
  <div class="card">
    <div class="form-book">
      <appInformations v-if="!check"/>
      <addBook v-if="check"/>
      <appFooter/>
    </div>
    <appBooks />
  </div>
</template>

<script>
import appHeader from "./components/appHeader.vue"
import appInformations from "./components/appInformations.vue"
import appBooks from "./components/appBooks.vue"
import addBook from "./components/addBook.vue"
import appFooter from "./components/appFooter.vue"
const loadedArray = localStorage.getItem("books");
let newBookArray ;
if(!loadedArray) {
  newBookArray = []
}
else {
  newBookArray = JSON.parse(loadedArray);
}
export default {
  
  components: {
    appHeader,
    appInformations,
    appBooks,
    addBook,
    appFooter
  },
  data(){
    return {
    providedData : {
      bookList : newBookArray
  },
    check : false,
    
    };
    
  },
  methods : {
    showAdd() {
      this.check = true;
    },
    showInformations(){
      this.check = false;
    },
    removeAll(){
      let arrayOfLenth = this.providedData.bookList.length
      for(let i = 0; i < arrayOfLenth;i++) {
        this.providedData.bookList.pop()
      }
    },
    removeBook(removedBook){
      this.providedData.bookList = this.providedData.bookList.filter((book) => book.key !== removedBook)
    }
  },
  provide() {
    return {
      providedData: this.providedData,  
      showAdd : this.showAdd,
      showInformations : this.showInformations,
      removeAll : this.removeAll,
      removeBook : this.removeBook,
      check : this.check,    
    };
  },
  updated(){
    localStorage.setItem("books",JSON.stringify(this.providedData.bookList));
  }
}


</script>

<style></style>
