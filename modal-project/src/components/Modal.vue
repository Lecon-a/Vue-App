<template>
    <div class="backdrop">
        <div class="modal" :class="{sale : theme === 'sale'}">
            <span class="close_modal" @click="toggleClose">X</span>
            <h1>{{ header }}</h1>
            <p>{{ text }}</p>
        </div>
    </div>
</template>

<script>
    export default {
        props: ['header', 'text', 'theme', 'toggleClose'],
    }
</script>

<style>
    .modal {
        display: flex;
        flex-direction: column;
        position: relative;
        width: 400px;
        padding: 16px 20px 20px;
        margin: 10rem auto;
        background: white;
        border-radius: 10px;
    }

    .backdrop {
        top: 0;
        position: fixed;
        background: rgba(0, 0, 0, .5);
        width: 100%;
        height: 100%;
    }
</style>