<template>
    <button class="animated" @click="click" :class="variant">
        <slot />
    </button>
</template>

<script>
export default {
    props: {
        variant: String
    },
    methods: {
        click() {
            this.$emit('onClick')
        }
    }
}
</script>

<style lang="scss">
    button.animated {
        padding: 10px 15px;

        border: 1px solid;
        border-radius: 4px;
        font-size: var(--fontsize-normal);

        &:disabled {
            cursor: not-allowed;
            color: var(--grey-600);
            border-color: var(--grey-400);
            background-color: var(--grey-200);
        }

        &:not([disabled]) {
            color: var(--grey-0);
            border-color: var(--main-color);
            background-color: var(--main-color);

            cursor: pointer;
            transition: .2s ease;

            &:hover {
                color: var(--main-color);
                background-color: var(--grey-0);

                transition: .2s ease;
            }

            &.outlined {
                color: var(--main-color);
                background-color: var(--grey-0);

                &:hover {
                    color: var(--grey-0);
                    background-color: var(--main-color);
                }
            }

            &:not(.outlined) {
                &.filled:hover {
                    color: var(--grey-0);
                    background-color: var(--main-color-darker);
                }
            }
        }
    }
</style>