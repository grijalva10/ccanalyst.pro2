<script>
  import "@spectrum-css/checkbox/dist/index-vars.css"
  import Field from "./Field.svelte"

  export let field
  export let label
  export let text
  export let disabled = false

  let fieldState
  let fieldApi

  const onChange = event => {
    fieldApi.setValue(event.target.checked)
  }
</script>

<Field
  {label}
  {field}
  {disabled}
  type="boolean"
  bind:fieldState
  bind:fieldApi
  defaultValue={false}>
  {#if fieldState}
    <div class="spectrum-FieldGroup spectrum-FieldGroup--horizontal">
      <label class="spectrum-Checkbox" class:is-invalid={!$fieldState.valid}>
        <input
          checked={$fieldState.value}
          disabled={$fieldState.disabled}
          on:change={onChange}
          type="checkbox"
          class="spectrum-Checkbox-input"
          id={$fieldState.fieldId} />
        <span class="spectrum-Checkbox-box">
          <svg
            class="spectrum-Icon spectrum-UIIcon-Checkmark75 spectrum-Checkbox-checkmark"
            focusable="false"
            aria-hidden="true">
            <use xlink:href="#spectrum-css-icon-Checkmark75" />
          </svg>
          <svg
            class="spectrum-Icon spectrum-UIIcon-Dash75 spectrum-Checkbox-partialCheckmark"
            focusable="false"
            aria-hidden="true">
            <use xlink:href="#spectrum-css-icon-Dash75" />
          </svg>
        </span>
        <span class="spectrum-Checkbox-label">{text || 'Checkbox'}</span>
      </label>
    </div>
  {/if}
</Field>

<style>
  .spectrum-Checkbox {
    width: 100%;
  }
</style>
