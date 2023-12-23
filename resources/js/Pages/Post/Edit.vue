<script setup>

</script>

<template>

        <h1 class="text-lg mb-8">Edit</h1>
        <div class="mb-8">
            <Link :href="route('post.index')" class="text-blue-500 text-sm mb-8">Back</Link>
        </div>
        <form @submit.prevent="update">
            <div class="mb-4">
                <input v-model="title" class="w-full rounded-full border-gray-300" type="text" placeholder="title">
            </div>
            <div class="mb-4">
                <textarea v-model="content" class="w-full rounded-full border-gray-300" placeholder="content"></textarea>
            </div>
            <div>
                <button class="hover:bg-white hover:text-blue-500 block p-2 w-32 border border-blue-500 bg-blue-500 rounded-full text-center text-white" type="submit">Update</button>
            </div>
        </form>

</template>

<script>
import {Link} from '@inertiajs/vue3'
import MainLayout from "@/Layouts/MainLayout.vue";
export default{
name: "Index",
    layout: MainLayout,

    props: [
        'post'
    ],

    components: {
       Link
    },

     data() {
        return {
            id: this.post.id,
            title: this.post.title,
            content: this.post.content,
        }
     },

     methods: {
        update(){
           this.$inertia.patch(`/posts/${this.id}`, {title: this.title, content: this.content})
        }
     }
}
</script>

<style scoped>

</style>
