<script lang="ts">
    // All images from the hiara folder
    const images = [
        '/images/hiara/hiara-2019.jpg',
        '/images/hiara/hiara-aparecida.jpg',
        '/images/hiara/hiara-bugados.jpg',
        '/images/hiara/hiara-coda.jpg',
        '/images/hiara/hiara-comeco.jpg',
        '/images/hiara/hiara-corsa.jpg',
        '/images/hiara/hiara-festa.jpg',
        '/images/hiara/hiara-formatura.jpg',
        '/images/hiara/hiara-garden.jpg',
        '/images/hiara/hiara-hacktown.jpg',
        '/images/hiara/hiara-ht.jpg',
        '/images/hiara/hiara-luzes.jpg',
        '/images/hiara/hiara-mox.jpg',
        '/images/hiara/hiara-natal.jpg',
        '/images/hiara/hiara-niver-mari.jpg',
        '/images/hiara/hiara-praia.jpg',
    ];

    // Split images into 3 rows
    function getRowImages(rowIndex: number) {
        const imagesPerRow = Math.ceil(images.length / 3);
        const start = rowIndex * imagesPerRow;
        const end = start + imagesPerRow;
        const rowImages = images.slice(start, end);
        
        // Duplicate images for infinite scroll effect
        return [...rowImages, ...rowImages, ...rowImages];
    }

    const row1 = getRowImages(0);
    const row2 = getRowImages(1);
    const row3 = getRowImages(2);
</script>

<div class="carousel-container">
    <!-- Row 1 - scrolls left -->
    <div class="carousel-row">
        <div class="carousel-track scroll-left">
            {#each row1 as image, i}
                <div class="image-wrapper">
                    <img 
                        src={image} 
                        alt="Hiara memory"
                        class="carousel-image"
                    />
                </div>
            {/each}
        </div>
    </div>

    <!-- Row 2 - scrolls right -->
    <div class="carousel-row">
        <div class="carousel-track scroll-right">
            {#each row2 as image, i}
                <div class="image-wrapper">
                    <img 
                        src={image} 
                        alt="Hiara memory"
                        class="carousel-image"
                    />
                </div>
            {/each}
        </div>
    </div>

    <!-- Row 3 - scrolls left -->
    <div class="carousel-row">
        <div class="carousel-track scroll-left">
            {#each row3 as image, i}
                <div class="image-wrapper">
                    <img 
                        src={image} 
                        alt="Hiara memory"
                        class="carousel-image"
                    />
                </div>
            {/each}
        </div>
    </div>
</div>

<style>
    .carousel-container {
        width: 100%;
        padding: 1rem 0;
        overflow: hidden;
        display: flex;
        flex-direction: column;
        gap: 0.5rem;
    }

    .carousel-row {
        width: 100%;
        overflow: hidden;
        position: relative;
    }

    .carousel-track {
        display: flex;
        gap: 0.5rem;
        width: fit-content;
    }

    .scroll-left {
        animation: scroll-left 30s linear infinite;
    }

    .scroll-right {
        animation: scroll-right 30s linear infinite;
    }

    .image-wrapper {
        position: relative;
        width: 150px;
        height: 150px;
        flex-shrink: 0;
        overflow: hidden;
        border-radius: 8px;
        box-shadow: 0 2px 8px rgba(0, 0, 0, 0.2);
        background: linear-gradient(135deg, #FAB5DA 0%, #EF61FA 100%);
    }

    .carousel-image {
        width: 100%;
        height: 100%;
        object-fit: cover;
        object-position: center;
        display: block;
    }

    @keyframes scroll-left {
        0% {
            transform: translateX(0);
        }
        100% {
            transform: translateX(-33.333%);
        }
    }

    @keyframes scroll-right {
        0% {
            transform: translateX(-33.333%);
        }
        100% {
            transform: translateX(0);
        }
    }

    /* Responsive adjustments */
    @media (max-width: 768px) {
        .image-wrapper {
            width: 120px;
            height: 120px;
        }

        .carousel-container {
            gap: 0.4rem;
        }

        .carousel-track {
            gap: 0.4rem;
        }
    }

    @media (max-width: 480px) {
        .image-wrapper {
            width: 100px;
            height: 100px;
            border-radius: 6px;
        }

        .carousel-container {
            gap: 0.3rem;
        }

        .carousel-track {
            gap: 0.3rem;
        }
    }

</style>
