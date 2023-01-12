<template>
    <div class="app-page" :id="id">
        <Header />

        <div class="main-area">
            <div class="main-content">

                <slot/>

            </div>
        </div>
    </div>
</template>

<script>
import Header from './Header.vue';
export default {
    components: {
        Header
    },
    props: {
        id: {
            type: String,
            required: true
        }
    }
}
</script>

<style lang="scss">
.app-page {
    .main-area {
        .main-content {
            width: 75vw;
            margin: 2vw auto;

            .row {
                display: flex;
                justify-content: space-between;
            }
        }
    }
}
</style>