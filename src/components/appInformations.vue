<template>
    <div class="head-form">

        <h2 id="count-head">
            <hr class="head-hr">
            <h2>Information</h2>
        </h2>

        <div class="informations">
            <div class="books-count">
                <div>Books</div>
                <div id="book-count-number">{{ providedData.bookList.length }}</div>
            </div>
            <div class="completed-books-count">
                <div>Completed Books</div>
                <div id="completed-count-number">{{ showCompletedBooks() }}</div>
            </div>
            <div class="total-pages">
                <div>Total Pages</div>
                <div id="book-page-number">{{ showTotalPages() }}</div>
            </div>
            <div class="completed-pages-count">
                <div>Completed Pages</div>
                <div id="completed-page-number">{{ showCompletedPages()}}</div>
            </div>
        </div>
        <hr class="head-hr">


    </div>

    <div class="submit-button">
        <button id="submit-ids" class="submit-add" @click="showAdd">Add New Book</button>
    </div>
    <div class="submit-button">
        <button id="remove-button-id" @click="removeAll">Remove All</button>
    </div>

</template>

<script>

export default {
    inject : ["showAdd","removeAll","providedData"],
    methods : {
        showCompletedBooks(){
            let count = 0;
            for (let i = 0; i < this.providedData.bookList.length;i++) {
                if (this.providedData.bookList[i].readed) {
                    count +=1;
                }
            }
            return count;
        },
        showTotalPages(){
            let count = 0;
            for (let i = 0; i < this.providedData.bookList.length;i++) {
                
                count += this.providedData.bookList[i].pages;
                
            }
            return count;
        },
        showCompletedPages(){
            let count = 0;
            for (let i = 0; i < this.providedData.bookList.length;i++) {
                if (this.providedData.bookList[i].readed) {
                    count += this.providedData.bookList[i].pages;
                }                
            }
            return count;
        }
    }    

}

</script>

<style></style>