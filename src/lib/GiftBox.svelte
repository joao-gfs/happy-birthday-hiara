<script>
    import { fade, fly } from 'svelte/transition';
    import { spring } from 'svelte/motion';

    let isOpen = false;

    function toggleOpen() {
        isOpen = !isOpen;
    }
</script>

<!-- svelte-ignore a11y-click-events-have-key-events -->
<!-- svelte-ignore a11y-no-static-element-interactions -->
<div class="gift-container" on:click={toggleOpen}>
    <div class="gift-box {isOpen ? 'open' : ''}">
        <div class="lid">
            <div class="ribbon-horizontal"></div>
            <div class="ribbon-vertical"></div>
        </div>
        <div class="box-body">
            <div class="ribbon-vertical"></div>
        </div>
        <img 
            src="/images/hiara/hiara-fundo-transparente-2.png" 
            alt="Hiara Surprise" 
            class="surprise-image {isOpen ? 'visible' : ''}"
        />
    </div>
</div>

<style>
    .gift-container {
        position: relative;
        width: 400px;
        height: 400px;
        margin: 50px auto;
        cursor: pointer;
        perspective: 1000px;
        display: flex;
        justify-content: center;
        align-items: flex-end;
    }

    .gift-box {
        position: relative;
        width: 300px;
        height: 300px;
        transform-style: preserve-3d;
    }

    /* Box Body */
    .box-body {
        position: absolute;
        bottom: 0;
        width: 100%;
        height: 100%;
        background-color: #9b59b6; /* Purple base */
        border-radius: 4px;
        z-index: 10;
        box-shadow: 0 10px 20px rgba(0,0,0,0.2);
    }

    /* Lid */
    .lid {
        position: absolute;
        top: 0;
        left: -20px; /* Slightly wider than box */
        width: calc(100% + 40px);
        height: 60px;
        background-color: #8e44ad; /* Darker purple */
        z-index: 20;
        border-radius: 8px;
        box-shadow: 0 2px 5px rgba(0,0,0,0.2);
        transition: transform 1.5s cubic-bezier(0.4, 0.0, 0.2, 1);
        transform-origin: top center;
    }

    /* Ribbons */
    .ribbon-vertical {
        position: absolute;
        left: 50%;
        height: 100%;
        width: 40px;
        background-color: #FA6461; /* bright-orange */
        transform: translateX(-50%);
    }

    .lid .ribbon-horizontal {
        position: absolute;
        top: 50%;
        width: 100%;
        height: 40px;
        background-color: #FA6461; /* bright-orange */
        transform: translateY(-50%);
    }

    /* Open Animation */
    .gift-box.open .lid {
        transform: translateY(-120px) rotateX(40deg);
        z-index: 0; 
    }

    /* Surprise Image */
    .surprise-image {
        position: absolute;
        bottom: 0;
        left: 50%;
        transform: translateX(-50%) scale(0.5);
        width: 100%; 
        height: auto;
        z-index: 5; 
        opacity: 0;
        transition: all 1.5s cubic-bezier(0.175, 0.885, 0.32, 1.275);
    }

    .gift-box.open .surprise-image {
        bottom: 200px;
        opacity: 1;
        /* Use translateZ to physically bring it in front of the lid in 3D space */
        transform: translateX(-50%) scale(1.1) translateZ(100px); 
        z-index: 100;
    }
    
    /* Refined Z-Index for simple 2D stacking illusion */
    /* 
       Closed:
       Lid (20)
       Box (10)
       Image (5) - hidden inside/behind
    */

    /*
       Open:
       Image pops up. Ideally it looks like it comes OUT of the box.
       If we want it to look like it comes OUT, it should be > Box but < Lid when passing through? 
       Actually, standard "jack in the box" usually has the image go in front of the back rim but behind the front rim.
       With simple 2D elements:
       If we put image z-index 15:
       It is in front of Box (10). 
       It is behind Lid (20).
       
       When 'open', Lid moves UP. Image moves UP.
       If Lid is 20, Image 15, Box 10. 
       Image will be on top of the box body color. This looks okay for a "pop in front" effect or "pop out of top".
       Let's stick with z-index 5 -> 30 for a "jump out completely" effect which is more fun for 2D.
    */
    
</style>
