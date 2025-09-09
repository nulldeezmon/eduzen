<script lang="ts">
  import Brand from "$lib/components/app/brand.svelte";
  import DashboardIcon from "@tabler/icons-svelte/icons/dashboard";
  import ServerIcon from "@tabler/icons-svelte/icons/cube";
  import TemplatesIcon from "@tabler/icons-svelte/icons/brand-graphql";
  import HelpIcon from "@tabler/icons-svelte/icons/help";
  import InnerShadowTopIcon from "@tabler/icons-svelte/icons/inner-shadow-top";
  import NodesIcon from "@tabler/icons-svelte/icons/server-2";
  import SearchIcon from "@tabler/icons-svelte/icons/search";
  import SettingsIcon from "@tabler/icons-svelte/icons/settings";
  import UsersIcon from "@tabler/icons-svelte/icons/users";
  import NavMain from "./nav-main.svelte";
  import NavSecondary from "./nav-secondary.svelte";
  import NavUser from "$lib/components/app/nav-user.svelte";
  import * as Sidebar from "$lib/components/ui/sidebar/index.js";
  import type { ComponentProps } from "svelte";
  const data = {
    user: {
      name: "shadcn",
      email: "m@example.com",
      avatar: "/avatars/shadcn.jpg",
    },
    navMain: [
      {
        title: "Dashboard",
        url: "dashboard",
        icon: DashboardIcon,
      },
      {
        title: "Servers",
        url: "servers",
        icon: ServerIcon,
      },
      {
        title: "Templates",
        url: "templates",
        icon: TemplatesIcon,
      },
      {
        title: "Nodes",
        url: "nodes",
        icon: NodesIcon,
      },
      {
        title: "Users",
        url: "users",
        icon: UsersIcon,
      },
    ],
    navSecondary: [
      {
        title: "Settings",
        url: "#",
        icon: SettingsIcon,
      },
      {
        title: "Get Help",
        url: "#",
        icon: HelpIcon,
      },
      {
        title: "Search",
        url: "#",
        icon: SearchIcon,
      },
    ],
  };
  let { ...restProps }: ComponentProps<typeof Sidebar.Root> = $props();
</script>

<Sidebar.Root collapsible="offcanvas" {...restProps}>
  <Sidebar.Header>
    <Sidebar.Menu>
      <Sidebar.MenuItem>
        <Sidebar.MenuButton class="data-[slot=sidebar-menu-button]:!p-1.5">
          {#snippet child({ props })}
            <a href="##" {...props}>
              <Brand class="font-semibold" />
            </a>
          {/snippet}
        </Sidebar.MenuButton>
      </Sidebar.MenuItem>
    </Sidebar.Menu>
  </Sidebar.Header>
  <Sidebar.Content>
    <NavMain items={data.navMain} />
    <NavSecondary items={data.navSecondary} class="mt-auto" />
  </Sidebar.Content>
  <Sidebar.Footer>
    <NavUser user={data.user} />
  </Sidebar.Footer>
</Sidebar.Root>
