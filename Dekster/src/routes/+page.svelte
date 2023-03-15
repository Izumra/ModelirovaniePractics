<script>
    // let matric=[
    //     [0,1,1,0,0],
    //     [0,0,0,1,0],
    //     [0,1,0,0,1],
    //     [0,0,1,0,0],
    //     [0,0,0,1,0]
    // ]
    // let tochka=0
    // let shag=0
    // let set=new Set()
    // const checkMatrick=()=>{
    //    for(let e=0;e<matric.length;e++){
    //             for(let j=0;j<matric.length;j++){
    //                 if(matric[e][j]==1&&j!=e){
    //                     console.log(`Из точки: ${tochka+1}, в точку ${j+1} можно пройти за: ${shag+1} шаг(ов)`)
    //                     set.add(j)
    //                 }
    //                 if(matric[e][j]==0&&j!=e){
    //                     for(let elem of set){
    //                         if(matric[elem][j]==1){
    //                             shag++
    //                             console.log(`Из точки: ${tochka+1}, в точку ${j+1} можно пройти за: ${shag+1} шаг(ов)`)
    //                         }
    //                         if(elem==set.size)shag=0
    //                     }
    //                 }
    //             }

    //         console.log(set)
    //    } 
    // }
    let massive=[4,5,7,2,8,9,12,14,12,14,11,12,15,12]
    let insertValue=0
    const createPils=()=>{
        massive[massive.length]=insertValue
        console.log(massive)
    }
    let pilaLegth=0
    let up=0
    let down=0
    const checkPils=()=>{
        for(let i=0;i<massive.length;i++){
            if(i>0&&massive[i]){
                massive[i-1]<=massive[i]?up++:down++
                if(pilaLegth<=(up+down)){
                    pilaLegth=up+down
                }
                if(up==down+2){
                    pilaLegth=down+up-1
                    up=0
                    down=0
                }
            }
        }
        if(pilaLegth==1)pilaLegth=0
        console.log(pilaLegth)
    }
</script>
<div class="matrik">
    <!-- {#if massive.length>0}
        {#each massive as s}
            <div class="">{s}</div>
        {/each}
        {massive}
    {/if} -->
    {massive}
</div>

<input type="number" bind:value={insertValue}>
<button on:click={createPils}>Add element</button>
<button on:click={checkPils}>Check pills</button>

<style>
    .matrik{
        border: 1px solid black;
        width: min-content;
        padding: 5px;
        margin-bottom: 10px;
    }
</style>