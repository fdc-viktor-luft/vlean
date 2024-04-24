<script lang="ts">
	import { page } from '$app/stores';

	let workdir: FileSystemDirectoryHandle | undefined = undefined;
	const onClick = async () => {
		workdir = await showDirectoryPicker().catch(() => undefined);
		if (!workdir) return;
		for await (const [key, value] of workdir.entries()) {
  			console.log({ key, value: value.kind === 'file' ? await value.getFile() : 'is dir' });
		}
	}
</script>

<div>
	<button on:click={onClick}>Click Me</button>
</div>

<style lang="scss">
	
</style>
