<script>
  import { Dropzone } from "@budibase/bbui"
  import { getContext } from "svelte"

  const { API } = getContext("sdk")
  const BYTES_IN_MB = 1000000

  export let files = []

  function handleFileTooLarge(fileSizeLimit) {
    alert(
      `Files cannot exceed ${fileSizeLimit /
        BYTES_IN_MB}MB. Please try again with smaller files.`
    )
  }

  async function processFiles(fileList) {
    let data = new FormData()
    for (let i = 0; i < fileList.length; i++) {
      data.append("file", fileList[i])
    }
    return await API.uploadAttachment(data)
  }
</script>

<Dropzone bind:files {processFiles} {handleFileTooLarge} />
