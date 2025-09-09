<template>

    <div class="card min-[1280px]:pl-0 min-[1280px]:pr-0 pl-4 pr-4" >
        <Menubar :model="items" class="!border-3 ">
            
            <template #start >   
                <img src="@/assets/logo.png" alt="Logo" class="h-10 mr-2"/>
            </template>
       
        </Menubar>
    </div>

</template>

<script>
import Menubar from 'primevue/menubar';


export default {
    components: { Menubar},
    data() {
        return {
            items: [
                {
                    label: 'Home',
                    url: '#/'
                },
                {
                    label: 'Technical',
                    url: '#/technical'
                },
                {
                    label: 'About',
                    url: '#/about'
                }
            ]
        };
    }
};

</script>