<script>
  import { backendUiStore } from "builderStore"
  import { goto, leftover } from "@sveltech/routify"
  import { onMount } from "svelte"

  onMount(async () => {
    // navigate to first table in list, if not already selected
    // and this is the final url (i.e. no selectedTable)
    if (
      !$leftover &&
      $backendUiStore.tables.length > 0 &&
      (!$backendUiStore.selectedTable || !$backendUiStore.selectedTable._id)
    ) {
      // this file routes as .../tables/index, so, go up one.
      $goto(`../${$backendUiStore.tables[0]._id}`)
    }
  })
</script>

{#if $backendUiStore.tables.length === 0}
  <i>Create your first table to start building</i>
{:else}<i>Select a table to edit</i>{/if}

<style>
  i {
    font-size: var(--font-size-m);
    color: var(--grey-5);
    margin-top: 2px;
  }
</style>
