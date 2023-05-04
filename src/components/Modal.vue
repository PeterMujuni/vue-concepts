<template>
    <div class="backdrop" @click.self="closeModal">
        <div class="modal" :class="{sale: theme === 'sale'}">
            <slot>Default content</slot>
            <div class="actions">
                <slot name="links"></slot>
            </div>
            <div class="inputFields">
                <slot name="inputFields"></slot>
            </div>
        </div>
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
    name: "Modal",
    props: {
        theme: String,
    },
    methods: {
        closeModal() {
            this.$emit('close')
        }
    }    
}) 

</script>

<style lang="scss">
    .backdrop {
        position: fixed;
        top: 0;
        background-color: rgba($color: #000000, $alpha: 0.7);
        width: 100%;
        height: 100%;

        .modal {
            width: 400px;
            padding: 20px;
            margin: 200px auto;
            background-color: white;
            border-radius: 10px;

            h1 {
                color: aqua;
                border: none;
                padding: 0;
            }

            &.sale {
                background-color: crimson;
                color: white;
                h1 {
                    color: white;
                }

                .actions {
                    color: white;
                    a {
                        color: white;
                    }
                }
            }
            .actions {
                text-align: center;
                margin: 30px 0 10px 0;

                a {
                    color: #333;
                    padding: 8px;
                    border: 1px solid #eee;
                    border-radius: 4px;
                    text-decoration: none;
                    margin: 10px;
                }
            }
            .inputFields {
                display: flex;
                flex-direction: column;
                gap: 1rem;
                align-items: center;
            }
        }
    }
</style>