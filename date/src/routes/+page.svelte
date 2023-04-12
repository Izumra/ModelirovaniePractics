<script lang="ts">
    let countHumans=0
    function randomIntFromInterval(min, max) {
        return Math.floor(Math.random() * (max - min + 1) + min)
    }
    const raschet=()=>{
        for(let i=0;i<countHumans;i++){
            let mounth=randomIntFromInterval(1,12)
            let year=randomIntFromInterval(-100000,2023)
            let day=0
            if(mounth==2&&year%4==0)day=randomIntFromInterval(1,28)
            else if(year%4==0&&mounth==2)randomIntFromInterval(1,29)
            else if(mounth%2==0)day=randomIntFromInterval(1,30)
            else day=randomIntFromInterval(1,31)
            console.log(`Человек ${i} родился ${day<10?'0'+day:day}.${mounth<10?'0'+mounth:mounth}.${year<0?year*(-1)+' до н.э.':year}`)
        }
        let difDays=1-(1/365);
        for(let i=3;i<=countHumans;i++){
            difDays*=(1-((i-1)/365))
        }
        console.log('Вероятность того, что двое или больше людей родились в один день одного месяца, но в разные годы:'+(1-difDays))
    }
</script>

<input bind:value={countHumans} type="number">
<button on:click={raschet}>Расчитать вероятность дня рождения двух и более людей в один день</button>