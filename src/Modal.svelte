<script>
  import { blur, fade, fly } from "svelte/transition";
</script>

<div class="modal-container" in:blur out:fade={{ duration: 100 }}>
  <div class="modal-content" in:fly={{ y: 1000, delay: 100 }}>
    <div in:fade={{ delay: 200 }}>
      <slot />
    </div>
  </div>
</div>
