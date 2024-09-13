<script lang="ts">
    import '../app.css';
    import Header from '$lib/components/Header.svelte';
    import Footer from '$lib/components/Footer.svelte';
</script>

<div class="flex flex-col min-h-screen">
    <Header />
    <main class="flex-grow container mx-auto mt-24 px-4">
        <slot />
    </main>
    <Footer />
</div>