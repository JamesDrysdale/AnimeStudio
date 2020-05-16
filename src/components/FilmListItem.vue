<template lang="html">
    <div class="filmlistitem">
        <p> {{ film.title }} </p>
    </div>
</template>

<script>
import { eventBus } from "@/main.js"

export default {
name: "film-list-item",
props: ["film"],

}
</script>

<style>

</style>