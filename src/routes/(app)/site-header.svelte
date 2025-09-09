<script lang="ts">
  import { Separator } from "$lib/components/ui/separator/index.js";
  import { Badge } from "$lib/components/ui/badge/index.js";
  import * as Sidebar from "$lib/components/ui/sidebar/index.js";
  import * as Breadcrumb from "$lib/components/ui/breadcrumb/index.js";
  import AlertCircle from "@tabler/icons-svelte/icons/alert-circle-filled";

  import { page } from "$app/state";
</script>

<header
  class="h-(--header-height) group-has-data-[collapsible=icon]/sidebar-wrapper:h-(--header-height) flex shrink-0 items-center gap-2 border-b transition-[width,height] ease-linear"
>
  <div class="flex w-full items-center gap-1 px-4 lg:gap-2 lg:px-6">
    <Sidebar.Trigger class="-ml-1" />
    <Separator
      orientation="vertical"
      class="mx-2 data-[orientation=vertical]:h-4"
    />
    <Breadcrumb.Root>
      <Breadcrumb.List>
        {#each page.url.pathname.split("/").slice(1, -1) as curpage}
          <Breadcrumb.Item class="capitalize">{curpage}</Breadcrumb.Item>
          <Breadcrumb.Separator />
        {/each}
        <Breadcrumb.Item>
          <Breadcrumb.Page class="capitalize"
            >{page.url.pathname.split("/").at(-1)}</Breadcrumb.Page
          >
        </Breadcrumb.Item>
      </Breadcrumb.List>
    </Breadcrumb.Root>

    <div class="ml-auto flex items-center gap-2">
      <Badge variant="destructive">
        <AlertCircle />
        <span>Administrative Control</span>
      </Badge>
    </div>
  </div>
</header>
