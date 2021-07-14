<template>
    <div>
        <b-modal id="editBookModal" title="Book Entry" ok-title="Save Book" @ok="onSubmit">
            <form action="#">
                <b-form-group
                label="Enter title"
                label-for="title"
                >
                <b-form-input id="title" v-model="book.title" trim></b-form-input>
                </b-form-group>

                <b-form-group
                label="Author"
                label-for="author"
                >
                <b-form-input id="author" v-model="book.author" trim></b-form-input>
                </b-form-group>

                <b-form-group
                label="Genre"
                label-for="genre"
                >
                <b-form-input id="genre" v-model="book.genre" trim></b-form-input>
                </b-form-group>

                <b-form-group
                label="Publisher"
                label-for="publisher"
                >
                <b-form-input id="publisher" v-model="book.publisher" trim></b-form-input>
                </b-form-group>

                <b-form-group
                label="Date Published"
                label-for="date_published"
                >
                <b-form-input id="date_published" type="date" v-model="book.date_published" trim></b-form-input>
                </b-form-group>

                <b-form-group
                label="No. of Pages"
                label-for="pages"
                >
                <b-form-input id="pages" v-model="book.pages" trim></b-form-input>
                </b-form-group>

                <b-form-group
                label="Shelf No."
                label-for="shelf_no"
                >
                <b-form-input id="shelf_no" v-model="book.shelf_no" trim></b-form-input>
                </b-form-group>

            </form>
        </b-modal>
    </div>
</template>
<script>
export default {
    props: {
        book: {}
    },
    methods: {
        async onSubmit() {
            this.$axios.put('https://lentrix.tk/lmdrl/api/books/'+this.book.id, this.book)
                .then((res)=>{
                    if(res.status==202) {
                        alert('Update successfully!!')
                    }
                })
                .catch((err)=> {
                    alert(err.message)
                })
        }
    }
}
</script>