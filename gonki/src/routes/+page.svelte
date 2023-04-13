<script>
    let countPlayers=0
    let firstispPogib=-1
    let secondPogib=-1
    let pogib=-1
    let vizhovshii=[]
    function randomIntFromInterval(min, max) {
        return Math.floor(Math.random() * (max - min + 1) + min)
    }
    const countVeroyat=()=>{
        for(let i=0;i<countPlayers;i++){
            pogib=-1
            let Fpov=randomIntFromInterval(0,100)
            if(Fpov<30&&firstispPogib==-1){
                firstispPogib=i
                console.log(`Гонщик ${i} погиб на первом испытании`)
                pogib=i
                continue
            }
            let Spov=randomIntFromInterval(0,100)
            if(Spov<60&&secondPogib==-1){
                secondPogib++
                console.log(`Гонщик ${i} погиб на втором испытании`)
                pogib=i
                continue
            }
            let oborudovanie=randomIntFromInterval(0,100)
            if(oborudovanie>40){
                console.log(`Гонщик ${i} погиб на третьем испытании при проезде через озеро без оборудования`)
                pogib=i
                continue
            }
            let smert=randomIntFromInterval(0,100)
            if(smert<20){
                console.log(`Гонщик ${i} погиб на последнем испытании`)
                pogib=i
                continue
            }
            if(pogib==-1){
                console.log(`Гонщик ${i} преодолел заезд без происшествий`)
                vizhovshii.push(i)
            }
        }
        pogib=-1
        console.log('Вероятность того, что выйграет участник равна: '+(0.7*0.4*0.4*0.8))
        console.log('Средняя вероятность выйгрыша каждого из участников: '+((0.7*0.4*0.4*0.8)*4))
    }
</script>

<input bind:value={countPlayers} type="number">
<button on:click={countVeroyat}>Расчитать вероятность</button>