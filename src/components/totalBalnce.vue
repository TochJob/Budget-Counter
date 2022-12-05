<template>
    <div class="total-value">
        <p class="total-value__current">Balance: {{total}} </p>
    </div>
</template>

<script>
export default {
    name: "TotalBalance",
    props: {
        total: {
            type: Number,
            default: 0
        }
    }
}
</script>
<style>

</style>