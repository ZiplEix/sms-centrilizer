<script lang="ts">
    import Icon from '@iconify/svelte';

    import ContactList from '$lib/ContactList.svelte';
    import ContactCard from '$lib/ContactCard.svelte';

    export let data: {contacts: {id: string, name: string, phone: string}[]};

    let drawerOpen = false;

    function toggleDrawer() {
        drawerOpen = !drawerOpen;
    }
</script>

<main class="flex h-screen overflow-hidden">
    <!-- Drawer -->
    <div class={`bg-base-200 h-full transition-width duration-200 flex flex-col ${drawerOpen ? 'w-48' : 'w-16'}`}>
        <!-- Menu Button -->
        <div class={`flex items-center ${drawerOpen ? "" : "justify-center"} m-4`}>
            <button class="hover:bg-base-300 p-2 rounded-md" on:click={toggleDrawer}>
                <Icon icon="ic:round-menu" class="text-3xl" />
            </button>
        </div>

        <!-- Espace pour pousser le contenu en bas -->
        <div class="flex-grow"></div>

        <!-- Navigation Links -->
        <div class="flex flex-col space-y-4 justify-start items-start px-2">
            <a href="#" class={`btn btn-ghost btn-sm w-full flex items-center ${drawerOpen ? "justify-start" : "justify-center"} space-x-2`}>
                <Icon icon="ic:round-home" class="text-3xl" />
                {#if drawerOpen}
                    <span>Home</span>
                {/if}
            </a>
            <a href="#" class={`btn btn-ghost btn-sm w-full flex items-center ${drawerOpen ? "justify-start" : "justify-center"} space-x-2`}>
                <Icon icon="ic:round-message" class="text-3xl" />
                {#if drawerOpen}
                    <span>Messages</span>
                {/if}
            </a>
            <a href="#" class={`btn btn-ghost btn-sm w-full flex items-center ${drawerOpen ? "justify-start" : "justify-center"} space-x-2`}>
                <Icon icon="ic:round-settings" class="text-3xl"/>
                {#if drawerOpen}
                    <span>Settings</span>
                {/if}
            </a>
        </div>

        <!-- Vertical Divider -->
        <div class="divider mx-2 my-1"></div>

        <!-- Profile Section -->
        <div class="flex flex-col space-y-4 justify-start items-start px-2 mb-4">
            <a href="#" class={`btn btn-ghost btn-sm w-full flex items-center ${drawerOpen ? "justify-start" : "justify-center"} space-x-2`}>
                <Icon icon="ic:round-account-circle" class="text-3xl" />
                {#if drawerOpen}
                    <span>Home</span>
                {/if}
            </a>
        </div>
    </div>


    <!-- Main Content -->
    <div class="flex-grow flex">
      <!-- Contacts List -->
        <div class="w-1/3 bg-base-100 border-r border-base-300 p-4 overflow-y-auto">
            <h2 class="text-lg font-semibold mb-4">Contacts</h2>
            <ContactList>
                {#each data.contacts as contact}
                    <ContactCard name={contact.name} phone={contact.phone} />
                {/each}
            </ContactList>
        </div>

      <!-- Message Content -->
        <div class="w-2/3 bg-base-100 p-4 overflow-y-auto">
            <h2 class="text-lg font-semibold mb-4">John Doe</h2>
            <div class="space-y-4">
                <div class="chat chat-start">
                    <div class="chat-bubble chat-bubble-primary">
                        Salut, comment vas-tu ?
                    </div>
                </div>
                <div class="chat chat-end">
                    <div class="chat-bubble chat-bubble-secondary">
                        Je vais bien, merci ! Et toi ?
                    </div>
                </div>
                <!-- Ajouter plus de messages ici -->
            </div>
        </div>
    </div>
</main>
