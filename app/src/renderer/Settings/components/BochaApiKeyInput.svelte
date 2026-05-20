<script lang="ts">
  import { createEventDispatcher } from 'svelte'

  export let value: string = ''
  const dispatch = createEventDispatcher<{ update: string }>()

  let visible = false

  function handleInput(event: Event) {
    const target = event.target as HTMLInputElement
    dispatch('update', target.value)
  }
</script>

<div class="wrapper">
  <h3>Bocha API Key</h3>
  <div class="input-wrapper">
    <input
      type={visible ? 'text' : 'password'}
      bind:value
      placeholder="Enter your Bocha API key"
      on:input={handleInput}
    />
    <button class="toggle-btn" on:click={() => (visible = !visible)}>
      {visible ? 'Hide' : 'Show'}
    </button>
  </div>
</div>

<style lang="scss">
  .wrapper {
    display: flex;
    align-items: center;
    justify-content: space-between;
    width: 100%;
    gap: 1rem;
  }

  h3 {
    line-height: 1;
    font-size: 1.2rem;
    font-weight: 500;
    color: light-dark(var(--color-text), var(--on-surface-dark, #cbd5f5));
    white-space: nowrap;
  }

  .input-wrapper {
    display: flex;
    align-items: center;
    gap: 0.5rem;
    flex: 1;
    max-width: 400px;
  }

  input {
    flex: 1;
    font-size: 1rem;
    line-height: 1;
    padding: 0.5rem;
    border-radius: 8px;
    border: 1px solid light-dark(var(--color-border), rgba(71, 85, 105, 0.4));
    background: light-dark(var(--color-background), var(--surface-elevated-dark, #1b2435));
    color: light-dark(var(--color-text), var(--on-surface-dark, #cbd5f5));
    font-family: monospace;
  }

  .toggle-btn {
    font-size: 0.9rem;
    padding: 0.4rem 0.8rem;
    border-radius: 6px;
    border: 1px solid light-dark(var(--color-border), rgba(71, 85, 105, 0.4));
    background: light-dark(var(--color-background), var(--surface-elevated-dark, #1b2435));
    color: light-dark(var(--color-text), var(--on-surface-dark, #cbd5f5));
    cursor: pointer;
    white-space: nowrap;

    &:hover {
      background: light-dark(var(--color-hover), rgba(71, 85, 105, 0.2));
    }
  }
</style>
