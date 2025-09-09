<script lang="ts">
  let { class: className, size = 6, ...restProps } = $props();
  import { cn } from "$lib/utils";
  import BrandIcon from "./brandicon.svelte";
</script>

<div
  class={cn(
    "tracking-tight text-2xl font-medium flex flex-row gap-1.5 items-center justify-center",
    className,
  )}
>
  <BrandIcon class="size-{size}" />
  <h1>Netite</h1>
</div>
