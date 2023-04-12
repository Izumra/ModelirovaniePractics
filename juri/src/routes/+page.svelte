<script>
    let juri1=5
    let juri2=2
    let verPrav1=0
    let verPrav2=0
    let reshenie=''
    let countP=0
    let countNep=0
    let p=0
    function randomIntFromInterval(min, max) {
        return Math.floor(Math.random() * (max - min + 1) + min)
    }
    const veroyat=()=>{
        for(let i=0;i<juri1;i++){
            if(i<3&&p<100&&p>0){
                let ver=randomIntFromInterval(0,100)
                ver<p?reshenie='правильное':reshenie='неправильное'
                if(reshenie=='правильное')countP++
                else countNep++
                console.log(`Жюрист ${i} вынес ${reshenie} решение`)
                reshenie=''
            }
            else{
                let ver=randomIntFromInterval(0,1)
                if(ver==0){
                    countP++
                    reshenie='правильное'
                }
                else{
                    countNep++
                    reshenie='неправильное'
                }
                console.log(`Жюрист ${i} вынес ${reshenie} решение`)
                if(i==juri1-1){
                    if(countP>countNep)console.log('Команда 1 вынесла правильное решение')
                    else console.log('Команда 1 вынесла неправильное решение')
                }
            }
        }
        countP=0
        countNep=0
        for(let i=0;i<juri2;i++){
            if(p<100&&p>0){
                let ver=randomIntFromInterval(0,100)
                ver<p?reshenie='правильное':reshenie='неправильное'
                if(reshenie=='правильное')countP++
                else countNep++
                console.log(`Жюрист ${i} вынес ${reshenie} решение`)
                reshenie=''
            }
            if(i==juri2-1){
                if(countP>countNep)console.log('Команда 2 вынесла правильное решение')
                else if(countP==countNep)console.log('Команда не определилась')
                else console.log('Команда 2 вынесла неправильное решение')
            }
        }
        console.log('Жюри из команды 1 выносят правильное решение с вероятностью '+((p/100)**3+(50/100)**2))
        console.log('Жюри из команды 2 выносят правильное решение с вероятностью '+((p/100)**2))
    }
</script>

<input bind:value={p} type="number">
<button on:click={veroyat}>Посчитать вероятность</button>
