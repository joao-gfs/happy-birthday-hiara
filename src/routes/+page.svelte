<script>
    import Carousel from "$lib/components/Carousel.svelte";
    import CardSpecial from "$lib/components/CardSpecial.svelte";
    import GiftBox from "$lib/GiftBox.svelte";
    import { base } from "$app/paths";
    import { onMount, onDestroy } from "svelte";
    import { fade } from "svelte/transition";

    let kuromi_base = `${base}/images/kuromi.webp`;
    let kuromi_hover = `${base}/images/kuromi-2.webp`;

    let hello_kitty_base = `${base}/images/hello-kitty.webp`;
    let hello_kitty_hover = `${base}/images/hello-kitty-2.webp`;

    let isKuromiHovered = false;
    let isHelloHovered = false;

    const images = [
        "hiara-formatura.jpg",
        "hiara-praia.jpg",
        "hiara-hacktown.jpg",
        "hiara-coda.jpg",
        "hiara-luzes.jpg",
    ];

    let currentImageIndex = 0;

    // Use onMount for interval to avoid SSR issues if any, though Svelte handles this well usually.
    // Also handling interval cleanup.
    onMount(() => {
        const interval = setInterval(() => {
            currentImageIndex = (currentImageIndex + 1) % images.length;
        }, 4000);

        return () => clearInterval(interval);
    });
</script>

<main>
    <audio src="{base}/harry-styles-adore-you.mp3">
        Ops, deu ruim. Vai cantando Adore You do Harry na sua cabeça
    </audio>

    <div class="flex flex-col gap-8 w-full pt-8 pb-[100px] px-8">
        <div
            class="flex flex-row justify-between items-center w-full max-w-full overflow-hidden"
        >
            <img
                src={isKuromiHovered ? kuromi_hover : kuromi_base}
                alt="Kuromi"
                class="h-[175px] w-auto object-contain shrink origin-bottom transition-transform duration-300
                       hover:animate-wiggle"
                on:mouseenter={() => (isKuromiHovered = true)}
                on:mouseleave={() => (isKuromiHovered = false)}
            />

            <div
                class="text-center font-title font-extrabold drop-shadow-[0_0_10px_rgba(255,255,255,0.3)] hover:drop-shadow-[0_0_10px_rgba(255,255,255,0.7)] grow px-2"
            >
                <h1 class="text-[50px] leading-none uppercase">
                    Feliz Aniversário
                </h1>
                <p class="text-[125px] leading-none tracking-widest uppercase">
                    Hiara!
                </p>
            </div>

            <img
                src={isHelloHovered ? hello_kitty_hover : hello_kitty_base}
                alt="Hello Kitty"
                class="h-[175px] w-auto object-contain shrink origin-bottom transition-transform duration-300
                       hover:animate-wiggle"
                on:mouseenter={() => (isHelloHovered = true)}
                on:mouseleave={() => (isHelloHovered = false)}
            />
        </div>
    </div>

    <div class="py-[40px] bg-grad-salmon">
        <Carousel />
    </div>

    <div>
        <CardSpecial />
    </div>

    <div class="mt-10">
        <div
            class="text-center font-title font-extrabold drop-shadow-[0_0_10px_rgba(255,255,255,0.3)] hover:drop-shadow-[0_0_10px_rgba(255,255,255,0.7)] grow px-2 text-[50px] leading-none uppercase"
        >
            <h2>O Aniversário é seu,</h2>
            <h2>mas na nossa vida, você é o presente</h2>
        </div>
        <div class="mt-50 py-12 flex justify-center items-center min-h-[600px]">
            <GiftBox />
        </div>
    </div>

    <div class="bg-grad-purple p-20 flex gap-8 items-center justify-between">
        <div
            class="font-sans font-extrabold drop-shadow-[0_0_10px_rgba(255,255,255,0.3)] grow px-2 text-[35px] leading-tight text-white w-1/2"
        >
            <p>Parabéns pelo seu dia!</p>
            <p>Te amo muito e sou grato pela sua vida.</p>
            <p>Desejo que seus dias sejam felizes e suas noites tranquilas.</p>
            <p>
                Obrigado por me fazer tão feliz e ser minha companhia para todas
                as horas.
            </p>
            <p>Feliz dia 2, o seu dia!</p>
        </div>
        <div
            class="w-1/2 h-[500px] relative rounded-2xl overflow-hidden"
        >
            {#key currentImageIndex}
                <img
                    src={`${base}/images/hiara/${images[currentImageIndex]}`}
                    alt="Hiara"
                    class="absolute inset-0 w-full h-full object-cover"
                    in:fade={{ duration: 1000 }}
                    out:fade={{ duration: 1000 }}
                />
            {/key}
        </div>
    </div>
</main>
