<script>
    import Card from "./Card.svelte";

    const special_text = [
        ["E", "sforçada", ", a mulher mais obstinada que conheço. Sua dedicação me inspira sempre."],
        ["S", "ensível", ", uma flor que merece todo cuidado"],
        ["P", "arceira", ", a melhor pessoa para se ter ao lado, torce sempre e acredita mais em mim que eu mesmo"],
        ["E", "legante", ", tem um bom gosto e sabe usá-lo"],
        ["C", "arinhosa", ", tem o melhor cafuné e o melhor abraço do mundo"],
        ["I", "nteligente", ", tem sempre ideias incríveis e consegue aprender tudo que quiser"],
        ["A", "tenciosa", ", sempre percebe os detalhes em tudo e nas pessoas"],
        ["L", "inda", ", a mulher mais bonita, seja arrumada ou logo depois de acordar, é um deleite para os olhos"]
    ]
</script>

<Card title = "Te admiro, porque você é">
    {#each special_text as [letra, palavra, descricao]}
        <p>
            <span class="font-title font-bold text-4xl mb-2 text-purple-shock tracking-widest leading-snug">{letra}</span>
            <span class="text-2xl text-purple-shock font-semibold">{palavra}</span>
            <span class="text-2xl">{descricao}</span>
        </p>
    {/each }
</Card>