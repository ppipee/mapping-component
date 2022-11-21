<script>
  import { getContext } from 'svelte'

  export let dataSource = []

  const { styleable, Provider } = getContext('sdk')
  const component = getContext('component')
</script>

<div use:styleable={$component.styles}>
  {#each dataSource as data, index}
    <Provider data={{ data, index, length: dataSource.length }}>
      <slot />
    </Provider>
  {/each}
</div>
