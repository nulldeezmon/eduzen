<script lang="ts">
  import * as Sidebar from "$lib/components/ui/sidebar/index.js";
  import AppSidebar from "./app-sidebar.svelte";
  import SideHeader from "./site-header.svelte";

  let { children } = $props();
</script>

<Sidebar.Provider
  style="--sidebar-width: calc(var(--spacing) * 72); --header-height: calc(var(--spacing) * 12);"
>
  <AppSidebar variant="inset" />
  <Sidebar.Inset>
    <SideHeader />
    <div class="w-full flex justify-center">
      <div class="w-full xl:w-4/5 xl:pt-6">{@render children?.()}</div>
    </div>
  </Sidebar.Inset>
</Sidebar.Provider>
