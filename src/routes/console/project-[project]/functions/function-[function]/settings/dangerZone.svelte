<script lang="ts">
    import { Box, CardGrid } from '$lib/components';
    import Heading from '$lib/components/heading.svelte';
    import { Button } from '$lib/elements/forms';
    import { toLocaleDateTime } from '$lib/helpers/date';
    import Delete from './deleteModal.svelte';

    import { func } from '../store';

    let showDelete = false;
</script>

<CardGrid danger>
    <Heading tag="h6" size="7">Delete Function</Heading>
    <p>
        The function will be permanently deleted, including all deployments associated with it. This
        action is irreversible.
    </p>
    <svelte:fragment slot="aside">
        <Box>
            <svelte:fragment slot="title">
                <h6 class="u-bold u-trim-1">{$func.name}</h6>
            </svelte:fragment>
            <p>Last Updated: {toLocaleDateTime($func.$updatedAt)}</p>
        </Box>
    </svelte:fragment>

    <svelte:fragment slot="actions">
        <Button secondary on:click={() => (showDelete = true)}>Delete</Button>
    </svelte:fragment>
</CardGrid>

<Delete bind:showDelete />
