<script>
    // Events modifiers
    // once - makes sure the event can only fire once (removes handler)
    // preventDefault - prevents the default action (run e.preventDefault())
    // self - only fires the event is the clicked element is the same as the one that the event was bound to

    export let isPromo = false;
    export let showModal = false;

</script>

{#if showModal}
    <!-- User the self modifier to make sure the event in only emitted when the backdrop itself is clicked, not descendants -->
    <div class="backdrop" class:promo={isPromo} on:click|self>
        <div class="modal">
            <slot name="title"></slot>
            <slot></slot>
        </div>
    </div>
{/if}

<style>
    .backdrop {
        background-color: rgba(0, 0, 0, 0.80);
        position: fixed;
        top: 0;
        left: 0;
        bottom: 0;
        right: 0;
    }

    .modal {
        background-color: white;
        position: absolute;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
        max-width: 300px;
        padding: 20px;
        border-radius: 10px;
    }

    .promo > .modal {
        background-color: crimson;
        color: white;
    }
</style>
