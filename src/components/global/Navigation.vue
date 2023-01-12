<template>
    <nav class="navigation">
        <ul>
            <li><Link to="/">Home</Link></li>
            <li><Link to="/store">Store</Link></li>
            <li><Link to="/contact">Contact</Link></li>
        </ul>
    </nav>
</template>

<script>
import Link from './Link.vue';
export default {
    components: {
        Link
    }
}
</script>

<style lang="scss">
nav.navigation {
    ul {
        display: flex;

        li {
            a {
                margin: 0 20px;

                font-size: var(--fontsize-normal);
            }
        }
    }
}
</style>