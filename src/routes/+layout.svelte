<script lang="ts">
    import type { LayoutData } from './$types';
    import "../styles.css"
    export let data: LayoutData;
</script>

<main>
    <header>
        <h1>Redbirds Analytics Nest</h1>
    </header>
    <div>
        <slot />
    </div>

    <footer>
        Product of Apostolos Mandelos & Mackenze Stathis
    </footer>
</main>

<style>
    header{
        background-color:var(--primary);
        padding: 1rem;
        display: grid;
        place-content: center;
    }

    h1{
        padding-top: 5px;
    }

    main{
        min-height: 100vh;
        display: flex;
        flex-direction: column;
    }
    div{
        flex: 1 auto;
    }

    footer{
        display: grid;
        place-content: center;
        padding: 2rem;
        font-size: 0.75rem;
        border-top: 1px solid rgb(174, 174, 174);
    }
</style>