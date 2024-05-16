<template>
    <div>
        <BookCardSlider :category="Test" :books="historyBooks" />
    </div>
</template>


<script>
import BookCardSlider from "./booksPageComponents/BooksSlider.vue";
import booksData from "../../src/data/books.json";

export default {
    components: {
        BookCardSlider,
    },
    data() {
        return {
            historyBooks: []   
        };
    },
    created() {
        // Populating book arrays based on category from JSON Data
        this.historyBooks = booksData.filter(book => book.category === 'History');

    }
}

</script>