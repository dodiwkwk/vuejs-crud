<template>
    <button ref="deleteNote" class="btn btn-text text-danger" @click="destroyNote">Delete</button>
</template>

<script>
import axios from 'axios'
export default {
    props: ['endpoint'],
    methods: {
        async destroyNote() {
           let q = window.confirm('Yakin')
           if (q == true) {
              let response = await axios.delete(`notes/${this.endpoint}/delete`)
              this.$toasted.show(response.data.message, {
                    type: 'success',
                    duration: 3000
                })
            this.$refs.deleteNote.parentNode.parentNode.remove()
           }
        }
    }
}
</script>