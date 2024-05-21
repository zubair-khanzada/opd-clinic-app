<template>
    <v-list density="compact" class="remainder-list">
        <NavigationItem v-for="(item) in data" :key="item.text" :text="item.text" :icon="item.icon" :className="item.className" />
    </v-list>
</template>

<script>

import NavigationItem from "@/components/NavigationItem.vue";

    export default {
        components: {
            NavigationItem
        },
        name: 'NavigationList',
        props: {
            data: {
                type: Array,
                required: true,
            },
        },
    }

</script>

<style scoped></style>