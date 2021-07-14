<template>
    <div>
        <b-modal id="deleteBookModal" title="Book Entry" ok-title="Delete Book" @ok="onDelete" ok-variant="danger">
            Are you sure you want to delete this book? <br>
            {{book.title}} <br> {{book.author}}
        </b-modal>
    </div>
</template>
<script>
export default {
    props: {
        book: {}
    },
    methods: {
        async onDelete() {
            this.$axios.delete('https://lentrix.tk/lmdrl/api/books/'+this.book.id)
            .then((res)=>{
                if(res.status==202) {
                    alert('Book deleted')
                    this.$emit('onDeleted')
                }
            })
        }
    }
}
</script>
