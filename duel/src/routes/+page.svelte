<script>
    let duelyant=''
    let strelyali=0
    let streluyayushii=[{person:1,procentPromaha:50,shansVigrisha:16.66,strelyal:false,killed:false},{person:2,procentPromaha:50,shansVigrisha:16.66,strelyal:false,killed:false},{person:3,procentPromaha:50,shansVigrisha:16.66,strelyal:false,killed:false},{person:4,procentPromaha:50,shansVigrisha:16.66,strelyal:false,killed:false},{person:5,procentPromaha:50,shansVigrisha:16.66,strelyal:false,killed:false},{person:6,procentPromaha:50,shansVigrisha:16.66,strelyal:false,killed:false}]
    let igra
    let alive=0
    const igraOkonchena=()=>{
        let vizhivshi=0
        for(let i=0;i<streluyayushii.length;i++){
            if(!streluyayushii[i].killed)vizhivshi+=1
        }
        alive=vizhivshi
        if(vizhivshi==1)console.log('Победа за дуэлянтом: '+duelyant)
        return vizhivshi!=1?false:true
    }
    const setduelyant=()=>{
        if(!streluyayushii[+duelyant-1].killed&&!streluyayushii[+duelyant-1].strelyal){
            let poop= 1 + Math.random() * (6 + 1 - 1);
            let vKogoStrelyali=Math.floor(poop);
            if(vKogoStrelyali==+duelyant||streluyayushii[vKogoStrelyali-1].killed||streluyayushii[+duelyant-1].killed){
                while(vKogoStrelyali==+duelyant||streluyayushii[vKogoStrelyali-1].killed||streluyayushii[+duelyant-1].killed){
                    poop= 1 + Math.random() * (6 + 1 - 1);
                    vKogoStrelyali=Math.floor(poop);
                }
            }
            let actionPopadaniya= 0 + Math.random() * (100 + 1);
            let releaseActionPopadaniya=Math.floor(actionPopadaniya);
            streluyayushii[+duelyant-1].strelyal=true
            strelyali++
            if(releaseActionPopadaniya<=streluyayushii[+duelyant-1].procentPromaha){
                let mes=[' попал смертельно в ',' попал не смертельно в ']
                let action= 0 + Math.random() * (1 + 1);
                let releaseAction=Math.floor(action);
                if(releaseAction==1){
                    let popadanie=['руку ','ногу ']
                    let actionp= 0 + Math.random() * (1 + 1);
                    let releasePopadanie=Math.floor(actionp);
                    console.log('Дуэлянт '+duelyant+mes[releaseAction]+popadanie[releasePopadanie]+"дуэлянта "+vKogoStrelyali+' с вероятностью попадания: '+streluyayushii[+duelyant-1].procentPromaha+'%' +" с общим шансом к выйгрышу: "+streluyayushii[+duelyant-1].shansVigrisha+"%")
                    if(releasePopadanie==0){
                        console.log('Умер '+vKogoStrelyali)
                        streluyayushii[vKogoStrelyali-1].procentPromaha-=50
                        streluyayushii[vKogoStrelyali-1].killed=true
                        if(streluyayushii[vKogoStrelyali-1].strelyal){
                            streluyayushii[vKogoStrelyali-1].strelyal=false
                            strelyali--
                        }
                    }
                    else{
                        streluyayushii[vKogoStrelyali-1].procentPromaha-=30
                        if(streluyayushii[vKogoStrelyali-1].procentPromaha<=0){
                            console.log('Умер '+vKogoStrelyali)
                            streluyayushii[vKogoStrelyali-1].killed=true
                            if(streluyayushii[vKogoStrelyali-1].strelyal){
                                streluyayushii[vKogoStrelyali-1].strelyal=false
                                strelyali--
                            }
                        }
                    }
                    streluyayushii[vKogoStrelyali-1].shansVigrisha*=(streluyayushii[vKogoStrelyali-1].procentPromaha/100)
                }
                else{
                    console.log('Дуэлянт '+duelyant+mes[releaseAction]+"дуэлянта "+vKogoStrelyali+' с вероятностью попадания: '+streluyayushii[+duelyant-1].procentPromaha+'%'+" с общим шансом к выйгрышу: "+streluyayushii[+duelyant-1].shansVigrisha+"%")
                    console.log('Умер '+vKogoStrelyali)
                    streluyayushii[vKogoStrelyali-1].killed=true
                    if(streluyayushii[vKogoStrelyali-1].strelyal){
                        streluyayushii[vKogoStrelyali-1].strelyal=false
                        strelyali--
                    }
                }
            }
            else{
                console.log('Дуэлянт '+duelyant+' промахнулся, стреляя в '+"дуэлянта "+vKogoStrelyali+' с вероятностью попадания: '+streluyayushii[+duelyant-1].procentPromaha+'%'+" с общим шансом к выйгрышу: "+streluyayushii[+duelyant-1].shansVigrisha+"%")
            }
        }
        else if(streluyayushii[+duelyant-1].killed){
            console.log('Дуэлянт '+(+duelyant) +' умер и не может стрелять')
        }
        else if(streluyayushii[+duelyant-1].strelyal){
            console.log('Дуэлянт '+(+duelyant)+' уже стрелял')
        }
        else if(igra==true){
            console.log('Игра окончена')
            for(let i=0;i<streluyayushii.length;i++){
                streluyayushii[i].killed=false
                streluyayushii[i].strelyal=false
            }
        }
        igraOkonchena()
        if(strelyali==alive){
            strelyali=0
            let strely=0
            for(let i=0;i<streluyayushii.length;i++){
                if(!streluyayushii[i].killed){
                    streluyayushii[i].strelyal=false
                    strely++
                }
            }
            console.log('--------------------------Раунд окончен---------------------------------------------')
            for(let i=0;i<streluyayushii.length;i++){
                if(!streluyayushii[i].killed)streluyayushii[i].shansVigrisha*=(100+(strely*10))/100
            }
        }
    }
</script>

<select on:blur={setduelyant} bind:value={duelyant}>
    <option value="1">Первый дуэлянт</option>
    <option value="2">Второй дуэлянт</option>
    <option value="3">Третий дуэлянт</option>
    <option value="4">Четвертый дуэлянт</option>
    <option value="5">Пятый дуэлянт</option>
    <option value="6">Шестой дуэлянт</option>
</select>