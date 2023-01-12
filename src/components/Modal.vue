<template>
    <div v-if="isOpen" class="modal-wrapper">
        <div class="modal-content" ref="modal">
            <slot />
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            listenerId: null
        }
    },
    props: {
        isOpen: {
            type: Boolean,
			required: true,
			default: false
        }
    },
    methods: {
        hasClickedOutside: function (target) {
            const modal = this.$refs.modal;
            if (!(modal instanceof HTMLDivElement)) return false;

            return !modal.contains(target);
        },
        handleOnClick: function (event) {
            if (this.hasClickedOutside(event.target))
                this.onClose();
        },
        onClose() {
            this.$emit('onClose');
        }
    },
    beforeUpdate: function() {
        if (this.isOpen)
            if (!this.listenerId)
                this.listenerId = document.addEventListener(
                    'click', this.handleOnClick);
        else
            this.listenerId && document.removeEventListener(
                'click', this.handleOnClick);
    }
}
</script>

<style lang="scss">
.modal-wrapper {
    position: fixed;
    z-index: 999999;
    top: 0;
    left: 0;
    bottom: 0;
    right: 0;

    background-color: rgba(0, 0, 0, .25);

    .modal-content {
        position: absolute;
        top: 50%;
        left: 50%;
        padding: 20px;

        background-color: var(--grey-0);

        transform: translate(-50%, -50%);
    }
}
</style>