<template>
    <v-list-item
        :class="className"
        color="primary"
    >
        <template v-slot:prepend>
            <v-icon :icon="icon"></v-icon>
        </template>
        <v-list-item-title v-text="text"></v-list-item-title>
    </v-list-item>
</template>

<script>

    export default {
        props: {
            text: {
                type: String,
                required: true,
            },
            icon: {
                type: String,
                required: true,
            },
            className: {
                type: String,
                required: false,
            },
        },
        name: 'NavigationItem',
    }

</script>

<style scoped></style>