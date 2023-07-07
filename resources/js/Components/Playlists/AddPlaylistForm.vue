<script setup>
import MyTextInput from '../MyTextInput.vue';
import { useForm } from '@inertiajs/vue3';
import PrimaryButton from '../PrimaryButton.vue';

const emit = defineEmits(['playlist-added']);

const form = useForm({
    title: '',
    //song: '', Adicionei o song ao form
});

function submit() {
    form.post(route('playlists.store'), { //tirei o add e coloquei o store
        onSuccess: () => {
            form.reset();
            emit('playlist-added');
        },
    });
}

</script>

<template>
    <form @submit.prevent="submit"> <!--- Adicionei submite no form, agora a opção de submite pega --->
        <fieldset class="border shadow-md p-2 rounded-md w-full m-auto">
            <legend class="font-bold">
                Add new Playlist
            </legend>
            <div>
                <MyTextInput v-model="form.title" label="Title" autofocus />
                <!--- <MyTextInput v-model="form.song" label="Song" autofocus /> // adicionei o v-model referente ao song e tbm coloquei o label para Song, se não ia ficar Song --->
                <PrimaryButton>Save</PrimaryButton>
            </div>
        </fieldset>
    </form>
</template>