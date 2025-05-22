<script lang="ts">
    export let text: string = '';
    export let value: string = '';
    export let type: string = 'text';
</script>

<div class="flex w-full items-center gap-2">
    <label class="w-40 text-left">{text}</label>
    <input
        class="flex-1 rounded border border-white px-1 py-1.5"
        {type}
        bind:value
    />
</div>