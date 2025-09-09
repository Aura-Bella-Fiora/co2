<template>

        <div class="flex-col gap-4 min-[1280px]:pl-0 min-[1280px]:pr-0 pl-4 pr-4">

                <div style=" position: relative; text-align: center; color: white;">
                        <img src="/src/assets/dorfAmFluss.png" class="flex min-[960px]:h-70 h-40 flex object-none w-full">
                        <div style="position: absolute; top: 50%; left: 50%; transform: translate(-50%, -50%)" class="flex min-[960px]:text-6xl text-3xl font-mono font-bold">
                                <img src="/src/assets/logo.png" class="h-10 min-[960px]:h-17" />Watchers
                        </div>
                </div>
        
                <h1 class="pt-6">Wer wir sind </h1>
                <p>
                        Co2-Watchers ist eine gemeinnützige Organisation, die es sich zur Aufgabe gemacht hat, den Co2 Ausstoß verschiedenster Unternehmen herauszufinden und einfach optisch darzustellen. </br>
                </p>
      

                 <div class="flex flex-col min-[960px]:flex-row break-words pt-6">
        
                        <div class="min-[960px]:w-1/4  min-[960px]:pl-2 min-[960px]:pr-2 pt-6">
                                <img src="/src/assets/Wissen-Zeichnung.png" class="h-auto w-50 mx-auto min-[960px]:w-50" style="border: none"></img>
                                <h1 style="color:blue">Wissen</h1>
                                <p>Nur mit ausreichen Informationen kann ein klarer Diskurs stattfinden.</p>
                        </div>

                        <div class="min-[960px]:w-1/4  min-[960px]:pl-2 min-[960px]:pr-2 pt-6" >
                                <img src="/src/assets/Informationen-Zeichnung.png" class="h-auto w-50 mx-auto min-[960px]:w-50" style="border: none"></img>
                                <h1 style="color:green">Informationen</h1>
                                <p>Klimadaten sollten für jeden frei zur Verfügung stehen. Sie sollten nicht durch Unternehmen oder die Regierung vertuscht werden.</p>
                        </div>

                        <div class="min-[960px]:w-1/4  min-[960px]:pl-2 min-[960px]:pr-2 pt-6"  >
                                <img src="/src/assets/Aufklärung-Zeichnung.png" class="h-auto w-50 mx-auto min-[960px]:w-50" style="border: none"></img>
                                <h1 style="color:orange">Aufklärung</h1>
                                <p>Nicht jeder ist sich über die Auswirkung bewusst, die unser aktueller Lebensstil und damit einhergehender Co2-Ausstoß verursacht.
                                        Daher ist es wichtig, Aufklärungsarbeit zu betreiben.
                                </p>
                        </div>
                
                        <div class="min-[960px]:w-1/4  min-[960px]:pl-2 min-[960px]:pr-2 pt-6">
                                <img src="/src/assets/Schaden-Zeichnung.png" class="h-auto w-50 mx-auto min-[960px]:w-50" style="border: none"></img>
                                <h1 style="color:red">Schaden</h1>
                                <p>Ein anhaltend hoher Co2-Ausstoß schadet nicht nur der Umwelt und besonders dem Klima, sondern auch dem Menschen. Ein verringerter Ausstoß sollte in aller Interesse sein.</p>
                        </div>

                </div>
      
      
                <h1 class="pt-6">Unsere gesammelten Daten:</h1>
                <p>     Wir sind stetig auf der Suche nach Co2-Daten von Unternehmen. Dabei verlassen wir uns nicht nur auf Aussagen der Unternehmen selbst, sondern greifen auch auf Schätzungen von unabhängigen
                        Wissenschaftlern zurück. <br/>
                        Die Emissionen in der folgenden Tabelle sind in Kilotonnen(kt) angegeben. 1kt = 1000 Tonnen. 
                </p>
                <custTable class="pt-6"></custTable>

        
                <div class="pt-15 pb-15">
                        <p>Weitere spannende Informationen findest du über die Links in folgendem Menü: </p>

                        <div :dir="langchecker()" class="grow">
                                <div class="w-50">
                                        <Menu :model="items" />
                                </div>
                        </div>
                

                        Das Menü wird nicht richtig dargestellt? Hier kannst du manuell zwischen rtl und ltr wechseln:
                        <Select v-model="selectedRTL" :options="layouts" optionLabel="name" placeholder="Select a layout" class="md:w-56" />

                </div>


        </div>    







</template>

<script>
import custTable from '/src/components/table.vue';
import navigations from '/src/components/navi.vue';
import footC from '/src/components/footer.vue';
import Select from 'primevue/select';
import Menu from 'primevue/menu';

export default {

  components: {
  custTable,
  navigations,
  footC,
  Select,
  Menu,
        },

    data() {
      
        return {
                modellll:'',
            lang: '',
            selectedRTL: null,
            layouts: [
                        { name: 'ltr'},
                        { name: 'rtl'},
                        ],

            items: [
                        { label: 'Technisches',
                        url: '#/technical'
                        },
                        { label: 'Methodik',
                        url: '#/methodik',
                        }
                        ]
                };
        }, 

      methods:{
                langchecker(){
                const rtlLangs = ['ar', 'he', 'fa', 'ur', 'ps', 'syr', 'dv'];
                if(rtlLangs.includes(navigator.language) && this.selectedRTL == null){
                        return 'rtl';
                        }
                else if(this.selectedRTL != null){
                        return this.selectedRTL.name;
                }
                else{
                        return 'ltr';
                        }
                }

    
        }       


}


</script>
