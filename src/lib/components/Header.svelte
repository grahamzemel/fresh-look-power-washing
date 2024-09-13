<script lang="ts">
    import { onMount } from 'svelte';
    
    let headerStyle = 'background-color: #60a5fa';  // Initial background color (blue-400)

    // Function to calculate the background color based on the scroll position
    function getBackgroundColor(scrollPosition) {
        if (scrollPosition >= 0 && scrollPosition < 200) {
            return '#60a5fa'; // blue-400
        } else if (scrollPosition >= 200 && scrollPosition < 400) {
            return '#5BACEB'; // blue-300
        } else if (scrollPosition >= 400 && scrollPosition < 600) {
            return '#57B0DE'; // blue-200
        } else if (scrollPosition >= 600 && scrollPosition < 800) {
            return '#53B5D3'; // teal-100
        } else if (scrollPosition >= 800 && scrollPosition < 1000) {
            return '#4EBAC6'; // teal-200
        } else if (scrollPosition >= 1000 && scrollPosition < 1200) {
            return '#4BBDBE'; // teal-300
        } else if (scrollPosition >= 1200 && scrollPosition < 1400) {
            return '#45C3B2'; // teal-400
        } else if (scrollPosition >= 1400 && scrollPosition < 1600) {
            return '#45C3B2'; // blue-400
        } else if (scrollPosition >= 1600 && scrollPosition < 1800) {
            return '#4BBDBE'; // blue-300
        } else if (scrollPosition >= 1800 && scrollPosition < 2000) {
            return '#4EBAC6'; // blue-200
        } else if (scrollPosition >= 2000 && scrollPosition < 2200) {
            return '#4EBAC6'; // teal-100
        } else if (scrollPosition >= 2200 && scrollPosition < 2400) {
            return '#53B5D3'; // blue-100
        } else {
            return '#53B5D3'; // blue-400 (default)
        }
    }

    onMount(() => {
        const handleScroll = () => {
            const scrollPosition = window.scrollY;
            const bgColor = getBackgroundColor(scrollPosition);  // Get the background color based on scroll
            headerStyle = `background-color: ${bgColor};`;  // Update the inline style
        };

        window.addEventListener('scroll', handleScroll);

        return () => {
            window.removeEventListener('scroll', handleScroll);
        };
    });
</script>

<!-- Use inline styles to apply dynamic background color -->
<nav style="{headerStyle}" class="p-6 fixed top-0 left-0 w-full z-10 transition-colors duration-300 ease-in-out">
    <div class="container mx-auto flex justify-between items-center pr-14 pl-14">
        <a href="#home" class="text-white text-2xl font-bold flex items-center">
            <img src="/logo.png" alt="Logo" class="h-8 w-8 mr-2" />
            Fresh Look Power Washing
        </a>
        <ul class="flex space-x-4">
            <li><a href="#home" class="text-white hover:text-blue-200">Home</a></li>
            <li><a href="#services" class="text-white hover:text-blue-200">Services</a></li>
            <li><a href="#contact" class="text-white hover:text-blue-200">Contact</a></li>
        </ul>
    </div>
</nav>
