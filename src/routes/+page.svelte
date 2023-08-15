<script>
    import '../styles.css'
</script>

<main>
    <section class="upload">
        <h2>Sheet Upload Form</h2>
        <form action="">
            <label for="inputSheet">
                input here:
                <input type="file">
            </label>
            <button type="submit">Submit Sheet</button>
        </form>
    </section>
</main>

<style>
    main{
        display: flex;
        flex-direction: column;
        flex: 1 auto;
        width: 100%;
    }

    .upload{
        width: 100%;
        border: 1px solid black;
        padding: 1rem;
        display: flex;
        flex-direction: column;
        gap: 1rem;
    }

    form{
        display: flex;
        flex-direction: column;
        gap: 2rem;
    }

    label{
        display: flex;
        gap: 1rem;
        font-size: 1.5rem;
    }

    button{
        width: max-content;
        background-color: var(--primary);
        padding: 0.5rem 1rem;
        border-radius: 1rem;
        font-size: 1.5rem;
    }

    h2{
        font-size: 2rem;
    }

    input{
        font-size: 1.5rem;
    }
</style>

