<script>
  // This component is overridden when running in a real app.
  // This simply serves as a placeholder component for the real screen router
  import { getContext } from "svelte"

  const { styleable } = getContext("sdk")
  const component = getContext("component")
</script>

<div use:styleable={$component.styles}>
  <h1>Screen Slot</h1>
  <span>
    The screens that you create will be displayed inside this box.
    <br />
    This box is just a placeholder, to show you the position of screens.
  </span>
</div>

<style>
  div {
    display: flex !important;
    flex-direction: column !important;
    align-items: center !important;
    justify-content: center !important;
    padding: 20px !important;
    text-align: center !important;
    border-style: dashed !important;
    border-width: 1px !important;
    color: #000000 !important;
    background-color: rgba(0, 0, 0, 0.05) !important;
  }
</style>
