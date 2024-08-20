<script lang='ts'>
    export let name: string;
    export let phone: string;
</script>

<li class="p-2 bg-base-200 rounded-lg hover:bg-base-300 cursor-pointer">
    <p class="font-medium">{ name }</p>
    <p class="text-sm text-gray-500">{ phone }</p>
</li>
