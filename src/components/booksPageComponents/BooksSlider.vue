<template>
    <div class="book-card-slider">
        <h2>{{ selectedGenre ? selectedGenre : 'All Books'}}</h2>

        <div class="filter-container">
            <select v-model="selectedGenre" v-on:change="filterBooks">
                <option value="">All Books</option>
                <option value="History">History</option>
                <option value="Fantasy">Fantasy</option>
                <option value="Childhood">Childhood</option>
            </select>
        </div>

        <div class="slider-container">
            <div v-for="(book, index) in filteredBooks" :key="index" class="book-card">
                <img :src="book.image" alt="book.title" class="book-cover">
                <div class="book-details">
                    <h4>{{ book.title }}</h4>
                    <p class="price">{{ book.price }}</p>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        props: {
            category: String,
            books: Array,
        },
        data() {
            return {
                selectedGenre: '',
                filteredBooks: this.books
            };
        },
        methods: {
            filterBooks() {
                if (this.selectedGenre) {
                    this.filteredBooks = this.books.filter(book => book.category === this.selectedGenre);
                } else {
                    this.filteredBooks = this.books;
                }
            }
        },
        watch: {
            books: {
                handler() {
                    this.filterBooks();
                },
                deep: true,
            }
        }
    };
</script>

<style scoped>

.book-card-slider {
    margin-bottom: 20px; 
}

.slider-container {
    display: flex;
    justify-content: center;
    gap: 50px; /* Adjust gap for better spacing on mobile */
    overflow-x: auto;
    background-color: var(--primary-colour);
    padding: 10px;
    width: 100%; /* Ensure it takes full width */
}

.book-card {
    flex: 0 0 auto;
    display: flex;
    flex-direction: column;
    align-items: center;
    border-radius: 10px;
    background-color: var(--secondary-colour);
    color: white;
    padding: 20px;
    width: 280px; /* Fixed width for consistency */
}

.book-cover {
    width: 100%;
    height: auto;
    object-fit: cover;
    border-radius: 8px;
}

.book-details {
    text-align: center;
    margin-top: 20px; /* Add some space between the image and the text */
}

.price {
    color: var(--fontColour-one);
}
</style>