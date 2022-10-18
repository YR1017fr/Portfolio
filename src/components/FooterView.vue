<template>
    <v-footer>
        <v-card elevation="0" rounded="0" width="100%" class="bg-black text-center">
            <v-card-text>
                <v-btn icon="fas fa-envelope" variant="plain" color="white" class="not-pointer"></v-btn>
                <span class="text-caption not-pointer">a27536625@gmail.com</span>
            </v-card-text>
            <v-card-text class="text-white not-pointer">
                @ {{new Date().getFullYear()}} -
                <strong>Raymond Wei All Rights Reserved</strong>
            </v-card-text>
        </v-card>
    </v-footer>
</template>

<script>
export default {

}
</script>

<style>
.v-footer {
    padding: 8px 0 !important;
}

.not-pointer {
    cursor: default !important;
}
</style>