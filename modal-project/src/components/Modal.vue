<template>
    <div class="backdrop">
        <span class="close_modal" @click.self="toggleClose">X</span>
        <div class="modal" :class="{sale : theme === 'sale'}">
           <slot></slot>
           <div class="modal_actions">
                <slot name="links"></slot>
           </div>
        </div>
    </div>
</template>

<script>
    export default {
        props: ['header', 'text', 'theme'],
        methods: {
            toggleClose() {
                this.$emit('close')
            }
        }
    }
</script>

<style>
    .modal {
        display: flex;
        flex-direction: column;
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