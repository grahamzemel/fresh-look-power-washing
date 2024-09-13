<script lang="ts">
    import { onMount } from 'svelte';
    import BeforeAfterGrid from '$lib/components/BeforeAfterGrid.svelte';

    let logoSrc = '/logo.png';
    let name = '';
    let email = '';
    let phone = '';
    let service = '';
    let message = '';
    let date = '';
    let time = '';

    const services = ['Power Washing', 'Car Washing', 'Deck Sealing', 'Weeding', 'Other'];

    function handleSubmit() {
        console.log({ name, email, phone, service, message, date, time });
        alert('Thank you for your message. We will get back to you soon!');
        name = '';
        email = '';
        phone = '';
        service = '';
        message = '';
        date = '';
        time = '';
    }

    const imagePairs = [
        { before: 'https://v0.dev/placeholder.svg?height=200&width=200', after: 'https://v0.dev/placeholder.svg?height=200&width=200' },
        { before: 'https://v0.dev/placeholder.svg?height=200&width=200', after: 'https://v0.dev/placeholder.svg?height=200&width=200' },
        { before: 'https://v0.dev/placeholder.svg?height=200&width=200', after: 'https://v0.dev/placeholder.svg?height=200&width=200' },
        { before: 'https://v0.dev/placeholder.svg?height=200&width=200', after: 'https://v0.dev/placeholder.svg?height=200&width=200' },
    ];

    onMount(() => {
        const today = new Date().toISOString().split('T')[0];
        document.getElementById('date').min = today;
    });
</script>

<svelte:head>
    <title>Fresh Look Power Washing</title>
</svelte:head>

<!-- Hero Section with a Soft Oceanic Gradient -->
<section id="home" class="bg-gradient-to-r from-blue-300 via-teal-100 to-blue-200 text-white py-12 mx-8 rounded-xl shadow-lg">
    <div class="container mx-auto px-16 py-12 flex flex-col md:flex-row items-center justify-between space-y-8 md:space-y-0">
        <div class="md:w-1/2 text-center md:text-left">
            <h1 class="text-5xl font-bold mb-6 text-gray-800">Welcome to Fresh Look Power Washing</h1>
            <p class="text-lg mb-8 text-gray-700">Get a fresh look for your home or business with our professional power washing services.</p>
            <button class="bg-teal-600 text-white px-8 py-4 rounded-lg text-xl hover:bg-teal-700 transition-colors" on:click={() => window.location.hash = 'contact'}>
                Get a Quote
            </button>
        </div>
        <div class="md:w-1/2 flex justify-center md:justify-end">
            <img src={logoSrc} alt="Fresh Look Power Washing Logo" class="w-64 h-64 md:w-80 md:h-80 rounded-full border-4 border-white shadow-lg" />
        </div>
    </div>
</section>

<!-- Divider with Wave Effect -->
<div class="w-full h-16 bg-wave-pattern"></div>

<!-- Before & After Section with Light Gradient Background -->
<section id="before-after" class="bg-gradient-to-b from-teal-200 to-blue-200 py-6 mx-8 rounded-xl shadow-lg">
    <div class="container mx-auto px-16 py-12 flex flex-col items-center">
        <h2 class="text-4xl font-bold text-teal-700 mb-12 text-center">Before & After</h2>
        
        <!-- Centering the Flexbox Layout -->
        <div class="flex flex-wrap justify-center items-center gap-6 w-full max-w-4xl">
            <!-- Ensure the grid inside the component is also centered -->
            <BeforeAfterGrid {imagePairs} />
        </div>
    </div>
</section>

<!-- Divider with Ocean Wave Effect -->
<div class="w-full h-16 bg-wave-pattern"></div>

<!-- Services Section with Off-White Background and Rounded Corners -->
<section id="services" class="bg-gradient-to-b from-blue-200 to-blue-500 py-6 mx-8 mb-16 rounded-xl shadow-lg">
    <div class="container mx-auto px-16 py-12">
        <h2 class="text-4xl font-bold text-blue-700 mb-12 text-center">Our Services</h2>
        <div class="grid grid-cols-1 md:grid-cols-2 gap-12">
            <div class="bg-white shadow-lg p-8 rounded-lg">
                <h3 class="text-3xl font-bold text-blue-700 mb-4">Power Washing</h3>
                <ul class="list-disc list-inside text-lg mb-6">
                    <li>Decks</li>
                    <li>Sidewalks</li>
                    <li>Driveways</li>
                    <li>Garages</li>
                    <li>Trash Cans</li>
                    <li>And More!</li>
                </ul>
                <p class="text-lg">Our professional power washing services will make your surfaces look brand new.</p>
            </div>
            <div class="bg-white shadow-lg p-8 rounded-lg">
                <h3 class="text-3xl font-bold text-blue-700 mb-4">Car Washing</h3>
                <p class="text-lg mb-6">Keep your vehicle looking its best with our thorough car washing services.</p>
                <ul class="list-disc list-inside text-lg">
                    <li>Exterior Wash</li>
                    <li>Interior Cleaning</li>
                    <li>Waxing</li>
                    <li>Detailing</li>
                </ul>
            </div>
            <div class="bg-white shadow-lg p-8 rounded-lg">
                <h3 class="text-3xl font-bold text-blue-700 mb-4">Deck Sealing</h3>
                <p class="text-lg">Protect your deck from the elements and enhance its natural beauty with our professional deck sealing services.</p>
            </div>
            <div class="bg-white shadow-lg p-8 rounded-lg">
                <h3 class="text-3xl font-bold text-blue-700 mb-4">Weeding</h3>
                <p class="text-lg">Keep your garden and landscape looking tidy with our weeding services.</p>
            </div>
        </div>
    </div>
</section>

<!-- Contact Section with Soft Blue Background -->
<section id="contact" class="bg-gradient-to-b from-blue-500 to-blue-200 py-6 text-white mx-8 rounded-xl shadow-lg">
    <div class="container mx-auto px-16 py-12">
        <h2 class="text-4xl font-bold mb-12 text-center">Contact Us</h2>
        <form on:submit|preventDefault={handleSubmit} class="max-w-lg mx-auto space-y-6">
            <div>
                <label for="name" class="block mb-2">Name:</label>
                <input type="text" id="name" bind:value={name} required class="w-full p-3 rounded-lg text-black" />
            </div>
            <div>
                <label for="email" class="block mb-2">Email:</label>
                <input type="email" id="email" bind:value={email} required class="w-full p-3 rounded-lg text-black" />
            </div>
            <div>
                <label for="phone" class="block mb-2">Phone:</label>
                <input type="tel" id="phone" bind:value={phone} required class="w-full p-3 rounded-lg text-black" />
            </div>
            <div>
                <label for="service" class="block mb-2">Service:</label>
                <select id="service" bind:value={service} required class="w-full p-3 rounded-lg text-black">
                    <option value="">Select a service</option>
                    {#each services as serviceOption}
                        <option value={serviceOption}>{serviceOption}</option>
                    {/each}
                </select>
            </div>
            <div>
                <label for="message" class="block mb-2">Message:</label>
                <textarea id="message" bind:value={message} rows="4" class="w-full p-3 rounded-lg text-black"></textarea>
            </div>
            <div>
                <label for="date" class="block mb-2">Preferred Date:</label>
                <input type="date" id="date" bind:value={date} required class="w-full p-3 rounded-lg text-black" />
            </div>
            <div>
                <label for="time" class="block mb-2">Preferred Time:</label>
                <input type="time" id="time" bind:value={time} required class="w-full p-3 rounded-lg text-black" />
            </div>
            <button type="submit" class="bg-teal-600 text-white px-6 py-3 rounded-lg text-xl hover:bg-teal-700 transition-colors">
                Send Message
            </button>
        </form>
    </div>
</section>

<!-- Footer Wave Divider -->
<div class="w-full h-16 bg-wave-pattern"></div>
