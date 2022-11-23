<script>
  import { getContext } from 'svelte'
  import isArray from 'lodash/isArray'
  import isEmpty from 'lodash/isEmpty'

  export let dataSource = []

  const { styleable, Provider } = getContext('sdk')
  const component = getContext('component')
</script>

<div use:styleable={$component.styles}>
  {#if isEmpty(dataSource)}
    a data source must have
  {:else if !isArray(dataSource)}
    a data source must be array
  {:else}
    {#each dataSource as data, index}
      <Provider data={{ data, index, length: dataSource.length }}>
        <slot />
      </Provider>
    {/each}
  {/if}
</div>
