<script>
    let showModal = true;
    let isPromo = true;
</script>

{#if showModal}
    <div class="backdrop" class:promo={isPromo}>
        <div class="modal">
            <p>Sign up for offers!</p>
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

    .promo > .modal{
        background-color: crimson;
        color: white;
    }
</style>
