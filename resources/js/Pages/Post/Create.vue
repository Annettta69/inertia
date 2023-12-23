<script setup>

</script>

<template>

        <h1 class="text-lg mb-8">Create</h1>
        <div class="mb-8">
            <Link :href="route('post.index')" class="text-blue-500 text-sm mb-8">Back</Link>
        </div>
        <form @submit.prevent="store">
            <div class="mb-4">
                <input v-model="title" class="w-full rounded-full border-gray-300" type="text" placeholder="title">
            </div>
            <div v-if="errors.title" class="text-red-500 text-sm">{{errors.title}}</div>
            <div class="mb-4">
                <textarea v-model="content" class="w-full rounded-full border-gray-300" placeholder="content"></textarea></div>
            <div v-if="errors.content" class="text-red-500 text-sm">{{errors.content}}</div>
            <div>
                <button class="hover:bg-white hover:text-blue-500 block p-2 w-32 border border-blue-500 bg-blue-500 rounded-full text-center text-white" type="submit">Store</button>
            </div>
        </form>

</template>

<script>
import {Link} from '@inertiajs/vue3'
import MainLayout from "@/Layouts/MainLayout.vue";
export default{
name: "Index",
    layout: MainLayout,
    components: {
       Link
    },

    props: [
        'errors'
    ],

     data() {
        return {
            title: '',
            content:'',
        }
     },

     methods: {
        store(){
            this.$inertia.post('/posts', {title: this.title, content: this.content})
        }
     }
}
</script>

<style scoped>

</style>
