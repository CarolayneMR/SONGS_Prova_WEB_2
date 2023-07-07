<script setup>
import MyTextInput from '../MyTextInput.vue';
import { useForm } from '@inertiajs/vue3';
import PrimaryButton from '../PrimaryButton.vue';

const emit = defineEmits(['song-added']);

const form = useForm({
    title: '',
    artist: '',
    album: '', //Algum tomou upgrade e virou alb
    genre: '',
});

function submit() {
    form.post(route('songs.store'), {
        onSuccess: () => {
            form.reset();
            emit('song-added');
        },
    });
}
</script>

<template>
    <form @submit.prevent="submit"> <!--- Adicionei a parte de submit --->
        <fieldset class="border shadow-md p-2 rounded-md w-full m-auto">
            <legend class="font-bold">
                Add new Song
            </legend>
            <div>
                <MyTextInput v-model="form.title" label="Title" autofocus />
                <MyTextInput v-model="form.artist" label="Artist" /> <!--- Adicionei o v-model para artista --->
                <MyTextInput v-model="form.album" label="Album" /> <!--- relacionei album corretamente agora --->
                <MyTextInput v-model="form.genre" label="Genre" />
                <PrimaryButton class="">Save</PrimaryButton>
            </div>
        </fieldset>
    </form>
</template>