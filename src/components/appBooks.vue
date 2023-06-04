<template>
    <div class="card-books" :class="{'autos' : providedData.bookList.length > 6, 'notautos' : providedData.bookList.length <=  6}">
        <div class="book" v-for="i in providedData.bookList" :key = "i.key">
            <div class="book-detail-piece">
                <h3>{{ i.bookName }}</h3>
            </div>
            <div class="book-detail-piece">
                <i></i><h3>{{ i.bookAuthor }}</h3>
            </div>
            <div class="book-detail-piece">
                <h3>{{ i.pages }}</h3>
            </div>
            <div class="book-detail-piece" v-if="i.readed">
                <button class="readed-button newreaded" @click="i.readed = false">Readed</button>
            </div>
            <div class="book-detail-piece" v-else>
                <button class="readed-button notreaded" @click="i.readed = true">Not readed</button>
            </div>
            <div class="book-detail-piece">
                <button class="remove-button" @click="removeBook(i.key)">Remove</button>
            </div>
        </div>
    </div>

</template>

<script>

export default {
    inject : ["providedData","removeBook"],
    methods : {

    },
    updated(){
        localStorage.setItem("books",JSON.stringify(this.providedData.bookList));
    }
}
</script>

<style>

</style>