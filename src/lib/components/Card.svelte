<script>
    let { title, children } = $props();
</script>

<div class="px-16 py-8">
    <div class="
        bg-pale-pink/70 
        text-black 
        p-8 
        rounded-[2.5rem] 
        backdrop-blur-md
        border border-white/35
        shadow-[inset_10px_-10px_20px_rgba(255,255,255,0.3),inset_-5px_5px_15px_rgba(0,0,0,0.05),0_10px_20px_rgba(0,0,0,0.05)]
    ">
        <h3 class="font-title font-bold text-3xl mb-2">{title}</h3>
        
        <div class="card-content">
            {@render children()}
        </div>
    </div>
</div>