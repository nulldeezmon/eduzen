<script lang="ts">
  import EllipsisIcon from "@tabler/icons-svelte/icons/dots";
  import { Button } from "$lib/components/ui/button/index.js";
  import * as DropdownMenu from "$lib/components/ui/dropdown-menu/index.js";
  import TrashIcon from "@tabler/icons-svelte/icons/trash";

  let { id, actions }: { id: string; actions: any } = $props();
</script>

<DropdownMenu.Root>
  <DropdownMenu.Trigger>
    {#snippet child({ props })}
      <Button
        {...props}
        variant="ghost"
        size="icon"
        class="relative size-8 p-0"
      >
        <span class="sr-only">Open menu</span>
        <EllipsisIcon />
      </Button>
    {/snippet}
  </DropdownMenu.Trigger>
  <DropdownMenu.Content>
    <DropdownMenu.Group>
      <DropdownMenu.Label>Actions</DropdownMenu.Label>
      {#each actions.actions as item}
        <DropdownMenu.Item
          onclick={() => item.action(id)}
          class="flex flex-row gap-2"
        >
          <item.icon />
          {item.label}
        </DropdownMenu.Item>
      {/each}
    </DropdownMenu.Group>
    <DropdownMenu.Separator />
    {#each actions.links as link}
      <DropdownMenu.Item>
        <a
          aria-label="Action"
          href={link.href(id)}
          class="flex flex-row gap-2 items-center"
        >
          <link.icon />
          {link.label}
        </a>
      </DropdownMenu.Item>
    {/each}
    <DropdownMenu.Separator />
    <DropdownMenu.Item
      onclick={() => actions.delete.action(id)}
      class="text-destructive"
    >
      <TrashIcon class="text-destructive" />
      {actions.delete.label}
    </DropdownMenu.Item>
  </DropdownMenu.Content>
</DropdownMenu.Root>
