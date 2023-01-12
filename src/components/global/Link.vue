<template>
    <router-link v-if="isRelativePath" :to="to" class="link" :class="variant">
        <slot/>
    </router-link>
    <a v-else :href="to" class="link" :class="variant">
        <slot/>
    </a>
</template>

<script>
export default {
    props: {
        to: {
            type: String,
            required: true,
            default: '/'
        },
        variant: {
            type: String,
            required: false
        }
    },
    computed: {
        isRelativePath: function() {
            return this.to[0] === '/';
        }
    }
}
</script>

<style lang="scss">
.link {
    transition: .2s ease;

    &:hover {
        color: var(--main-color);
        transition: .2s ease;
    }

    &.underline {
        position: relative;

        &::after {
            position: absolute;
            content: '';
            left: 0;
            bottom: -2px;

            width: 100%;
            height: .1px;

            background-color: var(--main-color);

            transition: .2s ease;
            transform: scaleX(0);
        }

        &:hover::after {
            transition: .2s ease;
            transform: scaleX(1);
        }
    }
}
</style>