<script>
  import { store } from "builderStore"
  import { Select } from "@budibase/bbui"

  export let value
</script>

<Select bind:value extraThin secondary on:change>
  <option value="">Choose an option</option>
  {#each $store.layouts as layout}
    <option value={layout._id}>{layout.name}</option>
  {/each}
</Select>
