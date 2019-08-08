<script>
  import uuidv1 from 'uuid/v1'
  import uuidv4 from 'uuid/v4'

  let currUuid = uuidv1()
  let optionsOpen = false
  let selectedOption = 'v1'

  function onClick() {
    let newUuid = ''
    if (selectedOption === 'v4') {
      newUuid = uuidv4()
    } else {
      newUuid = uuidv1()
    }

    currUuid = newUuid
  }

  function handleRadio(e) {
    selectedOption = e.target.value
  }

  const toggleOptions = () => (optionsOpen = !optionsOpen)
</script>

<div class="p-0 m-4 container-fluid">
  <div class="row">
    <div class="col-12 col-sm-9 col-md-7 col-lg-6 col-xl-5">
      <div class="card">
        <div class="card-body">
          <h5 class="card-title">Generate a uuid</h5>
          <p class="card-text">
            Simple UI to generate and display a uuid.
            <button 
              type="button" 
              class="btn btn-outline-secondary" 
              on:click={toggleOptions}
            >
              Options {#if !optionsOpen}+{:else}-{/if}
            </button>
          </p>
          {#if optionsOpen}
            <div class="form-group" on:change={handleRadio}>
              <div class="form-check form-check-inline">
                <input class="form-check-input" type="radio" name="inlineRadioOptions" id="v1" value="v1" bind:group={selectedOption}>
                <label class="form-check-label" for="v1">v1</label>
              </div>
              <div class="form-check form-check-inline">
                <input class="form-check-input" type="radio" name="inlineRadioOptions" id="v4" value="v4" bind:group={selectedOption}>
                <label class="form-check-label" for="v4">v4</label>
              </div>
            </div>
          {/if}
          <div class="form-group">
            <input class="form-control" type="text" bind:value={currUuid}>
          </div>
          <button type="button" class="btn btn-primary btn-block" on:click={onClick}>Generate</button>
        </div>
      </div>
    </div>
  </div>
</div>
