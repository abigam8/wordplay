<script lang="ts">
    import { browser } from '$app/environment';
    import { goto } from '$app/navigation';
    import Writing from '@components/app/Writing.svelte';
    import { getUser } from '@components/project/Contexts';
    import Profile from '../login/Profile.svelte';

    const user = getUser();

    // Go to the login page if on the profile and not logged in.
    $effect(() => {
        if (browser && $user === null) goto('/login');
    });
</script>

<!-- Is the user logged in?  -->
<Writing>
    {#if $user}
        <!-- Show their profile. -->
        <Profile user={$user} />
    {/if}
</Writing>
