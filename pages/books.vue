<template>
    <div>
        <NavBar />
        <EditBookModal :book="selectedBook" />
        <DeleteBookModal :book="selectedBook" @onDeleted="getAll"/>
        <div class="container">
            <h1>
                Books
                <BookEntryModal class="float-right" @onAdd="getAll"/>
            </h1>

            <table class="table table-bordered table-stripped">
                <thead>
                    <tr class="bg-info text-white">
                        <th>ID</th>
                        <th>Title</th>
                        <th>Author</th>
                        <th>Genre</th>
                        <th>Publisher</th>
                        <th>Date Published</th>
                        <th>Pages</th>
                        <th>Shelf No.</th>
                        <th>&nbsp;</th>
                        <th>&nbsp;</th>
                    </tr>
                </thead>
                <tbody>
                    <tr v-for="book in books" :key="book.id">
                        <td>{{book.id}}</td>
                        <td>{{book.title}}</td>
                        <td>{{book.author}}</td>
                        <td>{{book.genre}}</td>
                        <td>{{book.publisher}}</td>
                        <td>{{book.date_published}}</td>
                        <td>{{book.pages}}</td>
                        <td>{{book.shelf_no}}</td>
                        <td>
                            <b-button @click="onEdit(book)" variant="info" size="sm">
                                Edit
                            </b-button>
                        </td>
                        <td>
                            <b-button @click="onDelete(book)" variant="danger" size="sm">
                                Delete
                            </b-button>
                        </td>
                    </tr>
                </tbody>
            </table>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            books: [],
            selectedBook: {}
        }
    },
    methods: {
        async getAll() {
            await this.$axios.get('https://lentrix.tk/lmdrl/api/books')
            .then((res)=>{
                if(res.status==200) {
                    this.books =res.data
                }
            })
        },
        onEdit(selectedBook) {
            this.selectedBook = selectedBook;
            this.$bvModal.show('editBookModal')
        },
        onDelete(selectedBook) {
            this.selectedBook = selectedBook;
            this.$bvModal.show('deleteBookModal')
        }
    },
    created() {
        this.getAll()
    }
}
</script>