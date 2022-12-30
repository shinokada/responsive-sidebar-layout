<script lang="ts">
  import '../app.postcss';
  import { page } from '$app/stores';
  import { onMount } from 'svelte';
  import {
    Navbar,
    NavBrand,
    NavLi,
    NavUl,
    NavHamburger,
    Sidebar,
    SidebarGroup,
    SidebarItem,
    SidebarWrapper,
    Drawer,
    CloseButton,
    SidebarDropdownWrapper
  } from 'flowbite-svelte';
  import { Cog } from 'svelte-heros-v2';
  import { sineIn } from 'svelte/easing';
  let drawerHidden: boolean = false;
  const toggleDrawer = () => {
    drawerHidden = false;
  };

  let divClass = 'w-full md:block md:w-auto pr-8';
  let ulClass = 'flex flex-col p-4 mt-4 md:flex-row md:space-x-8 md:mt-0 md:text-lg md:font-medium';
</script>

<Navbar let:hidden let:toggle>
  <NavHamburger on:click={toggleDrawer} btnClass="ml-3 lg:hidden" />
  <NavBrand href="/" class="lg:ml-64">
    <Cog />
    <span class="self-center whitespace-nowrap text-xl font-semibold dark:text-white pl-4">
      My Website
    </span>
  </NavBrand>
  <NavHamburger on:click={toggle} />
  <NavUl {hidden} {divClass} {ulClass}>
    <NavLi href="/">Home</NavLi>
    <NavLi href="/pages/about">About</NavLi>
    <NavLi href="https://github.com/shinokada/flowbite-sveltekit-responsive-sidebar-layout"
      >GitHub</NavLi
    >
  </NavUl>
</Navbar>
<slot />
