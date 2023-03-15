<script>
    import { crossfade, slide,draw } from "svelte/transition";
    import { bounceIn } from 'svelte/easing';
    let view=false
    const min=2
    const max=32 
    let one=0
    let two=0
    let num=0
    let obs=0
    let veroyztnost=0
    const randomNumbers=()=>{
        let rand = min + Math.random() * (max + 1 - min)
        let rand1 = min + Math.random() * (max + 1 - min)
        //первая рандомная грань    
        one=Math.floor(rand)
        //вторая рандомная грань 
        two=Math.floor(rand1)
        view=true
        obs=one+two
        //формула расчета вероятности выпадения суммы чисел
        veroyztnost=1/(one*two)
    }
</script>

<input type="number" placeholder="Введите общее число на двух гранях" bind:value={num}>

<div class="cubic-wrap">
    {#if view}
        <div transition:slide={{duration:3000,easing:bounceIn}} class="cubic">{one}</div>
        <div transition:slide={{duration:3000,easing:bounceIn}} class="cubic">{two}</div>
        Общее число: {obs}
    {/if}
</div>

<button on:click={randomNumbers}>Бросить кости</button>
Вероятность выпадения данной суммы чисел:{veroyztnost}

<style>
    .cubic-wrap{
        width:170px;
        height:60px;
        display: flex;
        flex-wrap: wrap;
        margin-top: 14px;
    }
    .cubic{
        width:50px;
        height:50px;
        border-radius: 10px;
        margin-right: 20px;
        background-color: bisque;
        border: 2px solid rgb(82, 82, 82);
        font-weight: 700;
        display:flex;
        justify-content: center;
        align-items: center;
    }
    button{
        margin-top: 20px;
        background-color:aquamarine;
        border:none;
        height:32px;
        cursor: pointer;
        font-weight: 700;
        padding: 0 16px;
        font-size: 16px;
        border-radius: 8px;
    }
</style>