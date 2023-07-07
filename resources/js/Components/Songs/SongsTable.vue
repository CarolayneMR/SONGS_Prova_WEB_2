<script setup>
import SongTR from './SongTableRow.vue';

defineProps({
    songs: {
        type: Array,
        required: true,
    },
});
</script>

<template>
    <table>
        <tr class="text-left">
            <th>Title</th>
            <th>Artist</th>
            <th>Album</th>
            <th>Genre</th>
        </tr>
        <SongTR v-for="song in songs" :song="song" :key="song.id" /> <!--- Adicione o song=song --->
    </table>
</template>