<template>


    <div class="head-form">
        <h2>Add a new Book</h2>
    </div>

    <div class="form-detail">

        <div class="form-name">
            <label for="book-name" class="labels">Book Title</label><br>
            <input type="text" name="book-name" class="book-name" placeholder="The Good Old Days"  v-model="newBook.bookName">
        </div>
        <div class="form-author">
            <label for="author-name" class="labels">Author Name</label><br>
            <input type="text" name="author-name" class="author-name" placeholder="Otto Bettmann" v-model="newBook.bookAuthor">
        </div>
        <div class="number-page">
            <label for="number-page" class="labels">Number of Page</label><br>
            <input type="number" name="author-name" class="number-page-value" min="1" placeholder="224" v-model="newBook.pages">
        </div>
        <div class="read">
            <input type="checkbox" class="checkbox-readed" v-model="newBook.readed"><br>
            <label>Readed</label>
        </div>
        <div class="submit-button">
            <button type="submit" id="submit-id" @click="addNewBook(newBook)">Submit</button>
        </div>
        <div class="submit-button">
            <button type="submit" class="back" @click="showInformations">Back</button>
        </div>

    </div>

</template>

<script>
    export default {
    inject : ["showInformations","providedData"],
    data()  {

        return {
            newBook : {bookName : "",bookAuthor : "",pages : 0,readed : false,key : new Date().getTime()}
        }
    },
    methods : {
        addNewBook(){
            if (this.newBook.bookName == "") {
                this.newBook.bookName = "unknown"
            }
            if (this.newBook.bookAuthor == "") {
                this.newBook.bookAuthor = "unknown"

            }
            this.providedData.bookList.push(this.newBook);
            this.newBook = {bookName : "",bookAuthor : "",pages : 0,readed : false,key : new Date().getTime()}
        }
    }

}

</script>