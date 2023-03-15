<script>
    const startMas=[
        ['','75','80','60','85'],
        ['100','6','7','3','5'],
        ['150','1','2','5','6'],
        ['50','3','10','20','1']
    ]
    const changeMas=[
        ['','75','80','60','85'],
        ['100','','','',''],
        ['150','','','',''],
        ['50','','','','']
    ]
    let stores=[100,150,50]
    let magazines=[75,80,60,85]
    let value=0
    let mag=0
    metka:for(let i=0;i<stores.length;i++){
        for(let j=mag;j<magazines.length;j++){
            if(stores[i]>=magazines[j]&&stores[i]>=0){
                stores[i]-=magazines[j]
                value=magazines[j]
                if((j)<magazines.length&&(i)<stores.length){
                    changeMas[i+1][j+1]=value.toString()
                }
                else{
                    changeMas[i][j]=value.toString()
                }
                mag++
            }
            else if(stores[i]<magazines[j]&&stores[i]>=0){
                value=stores[i]
                magazines[j]-=stores[i]
                stores[i]=0
                if((j)<magazines.length&&(i)<stores.length){
                    changeMas[i+1][j+1]=value.toString()
                }
                else{
                    changeMas[i][j]=value.toString()
                }
                continue metka
            }            
        }
    }
</script>

<div class="">
    Исходный материал:    
</div>

<div class="zadacha">
    {#each startMas as stroke}
        {#each stroke as elem}
            <div class="el">{elem}</div>
        {/each}
    {/each}
</div>

<div class="">
    Решение транспортной задачи:    
</div>

<div class="zadacha">
    {#each changeMas as stroke}
        {#each stroke as elem}
            <div class="el">{elem}</div>
        {/each}
    {/each}
</div>

<style>
    .el{
        border: 1px solid rgb(0, 141, 124);
        display: flex;
        justify-content: center;
        align-items: center;
        width:30px;
        height:30px;
    }
    .zadacha{
        width:180px;
        display: flex;
        flex-wrap: wrap;
    }
</style>