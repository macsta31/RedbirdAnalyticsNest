<script lang="ts">
    import type { LayoutData } from './$types';
    import "../styles.css"
    export let data: LayoutData;
    import { dev } from '$app/environment';
    import { inject } from '@vercel/analytics';
    import { sideOfBall } from '$lib/ballsStore';
 
    inject({ mode: dev ? 'development' : 'production' });
    
    function setSide(side:string){
        sideOfBall.set(side)
    }

</script>

<main>
    <header>
        <h1>Redbirds Analytics Nest</h1>
        <nav>
            <li><button on:click={() => setSide('offence')} >Offence</button></li>
            <li><button on:click={() => setSide('defence')} >Defence</button></li>
        </nav>
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
        display: flex;
        flex-direction: column;
        align-items: center;
        gap: 1rem;
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

    nav{
        list-style-type: none;
        display:flex;
        align-items: center;
        justify-content: center;
        gap:1rem;
        width: 100%;
    }

    button{
        background-color: white;
        padding: 0.5rem 1rem;
        border-radius: 1rem;
    }
</style>