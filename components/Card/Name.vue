<template>
    <div class="card">
        <h4>{{name}}</h4>
        <p @click="$emit('remove', name)">x</p>
    </div>
</template>

<script setup>
const props = defineProps({
    name: String
})

</script>