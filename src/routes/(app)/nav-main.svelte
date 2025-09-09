<script lang="ts">
  import CirclePlusFilledIcon from "@tabler/icons-svelte/icons/circle-plus-filled";
  import MailIcon from "@tabler/icons-svelte/icons/mail";
  import { Button } from "$lib/components/ui/button/index.js";
  import * as Sidebar from "$lib/components/ui/sidebar/index.js";
  import type { Icon } from "@tabler/icons-svelte";
  let { items }: { items: { title: string; url: string; icon?: Icon }[] } =
    $props();
  import { page } from "$app/stores";

  function whatPage(): string {
    return $page.url.pathname.split("/").at(2) || "";
  }
</script>

<Sidebar.Group>
  <Sidebar.GroupContent class="flex flex-col gap-2">
    <Sidebar.Menu>
      {#each items as item (item.title)}
        <Sidebar.MenuItem>
          <a href={`/admin/${item.url}`} class="text-black dark:text-white">
            <Sidebar.MenuButton
              tooltipContent={item.title}
              class={whatPage() === item.url ? "bg-accent" : ""}
            >
              {#if item.icon}
                <item.icon />
              {/if}
              {item.title}
            </Sidebar.MenuButton>
          </a>
        </Sidebar.MenuItem>
      {/each}
    </Sidebar.Menu>
  </Sidebar.GroupContent>
</Sidebar.Group>
