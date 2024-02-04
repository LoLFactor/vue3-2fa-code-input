<script setup lang="ts">
import SidebarLink from '@/components/docs/SidebarLink.vue';
</script>

<template>
  <div class="flex grow flex-col gap-y-5 overflow-y-auto bg-white dark:bg-gray-900 px-6">
    <h1 class="dark:text-white py-4">Vue3 2FA Code Input</h1>
    <nav class="flex flex-1 flex-col">
      <ul role="list" class="flex flex-1 flex-col gap-y-7">
        <li>
          <ul role="list" class="-mx-2 space-y-1">
            <li>
              <SidebarLink href="#autofocus">Autofocus</SidebarLink>
              <SidebarLink href="#length">Length</SidebarLink>
              <SidebarLink href="#copy-paste">Copy-Paste</SidebarLink>
              <SidebarLink href="#immediate-updates">Immediate updates</SidebarLink>
              <SidebarLink href="#styling">Styling</SidebarLink>
            </li>
          </ul>
        </li>
      </ul>
    </nav>
  </div>
</template>
