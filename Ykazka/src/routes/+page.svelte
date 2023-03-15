<script>
    let countYkazok=0
    let values=[0,0,0]
    let prostoiTri=0
    let pryamoygolTri=0
    let ravnobedrennii=0
    let veroyatnostProst=0
    let veroyatnostRavnobed=0
    let veroyatnostPryamougol=0
    const breakYkazky=()=>{
        let min=0
        let max=30
        for(let i=0;i<3;i++){
            let rand = min + Math.random() * (max + 1 - min);
            let kusok=Math.floor(rand)
            max=kusok
            values[i]=kusok
        }
        let maxLength=values.indexOf(Math.max(...values))
        let indexStoron=''
        for(let i=0;i<3;i++)if(maxLength!=i)indexStoron+=i
        if(values[0]==values[1]||values[1]==values[2]||values[0]==values[2]){
            ravnobedrennii++
            countYkazok++
            if(ravnobedrennii==1){
                veroyatnostRavnobed=ravnobedrennii*(ravnobedrennii/countYkazok)+prostoiTri*(prostoiTri/countYkazok)+pryamoygolTri*(pryamoygolTri/countYkazok)
            }
        }
        else if(values[maxLength]*values[maxLength]==values[+indexStoron[0]]*values[+indexStoron[0]]+values[+indexStoron[1]]*values[+indexStoron[1]]){
            countYkazok++
            pryamoygolTri++
            if(pryamoygolTri==1){
                veroyatnostPryamougol=ravnobedrennii*(ravnobedrennii/countYkazok)+prostoiTri*(prostoiTri/countYkazok)+pryamoygolTri*(pryamoygolTri/countYkazok)
            }
        }
        else{
            countYkazok++
            prostoiTri++
            if(prostoiTri==1){
                veroyatnostProst=ravnobedrennii*(ravnobedrennii/countYkazok)+prostoiTri*(prostoiTri/countYkazok)+pryamoygolTri*(pryamoygolTri/countYkazok)
            }
        }
    }
</script>

<button on:click={breakYkazky}>Сломать указку</button>


<div class="">
    Сломано указок: {countYkazok}
</div>

<div class="">
    Нужно сломать указок в среднем для получения Обычного треугольника:{veroyatnostProst}
    {prostoiTri} 
</div>

<div class="">
    Нужно сломать указок в среднем для получения Прямого треугольника:{veroyatnostPryamougol}
    {pryamoygolTri}
</div>

<div class="">
    Нужно сломать указок в среднем для получения Равнобедренного треугольника:{veroyatnostRavnobed} 
    {ravnobedrennii}
</div>