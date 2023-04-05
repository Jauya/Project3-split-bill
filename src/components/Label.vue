<script setup>
const props = defineProps(['title','value']);

</script>
<template>
    <div>
        <span class="title">{{ props.title }}</span>
        <span class="value">{{ 
            new Intl.NumberFormat("en-US", {
                style: "currency",
                currency: "USD",
            }).format(props.value)
        }}</span>
    </div>
</template>

<style scoped>
.title{
    font: 900;
}

.value{
    color: yellowgreen;
}
</style>