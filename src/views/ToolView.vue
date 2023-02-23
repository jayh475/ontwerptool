<template>
    <header> <p class="title">Eigenschappen - tablad met velden</p> </header>
    <nav></nav>
  

    <div class="grid_container_editor">
        <div class="grid_item_left">

            <div style="display:flex;flex;justify-content: space-evenly; margin-bottom: 2%;margin-top:2%">
                <p> kruimelpad en titel:</p>
                <input type="text" v-model="kruimeldpad">
            </div>

            <div style="display:flex;flex;justify-content: space-evenly; margin-bottom: 2%;">
                <p>header afbeelding:</p>
                <input type="file" @change="handleFileUpload">
            </div>

            <div style="display:flex;flex;justify-content: space-evenly; margin-bottom: 2%;">
                <p>Header titel en code:</p>
                <input type="text" v-model="headerTitelCode">
            </div>

            
           
            <p>header:subtitel en code</p>
            <p>Header:subtitel en code</p>
            <p>Header:detail (label en waarde)</p>
            <p>Tabladen</p>
            <p>Acties</p>

        </div>
        <div class="grid_item_right">
            <p>veldgroep</p>

            <p>veldtype:codetabel</p>
            <p>Veldtype:datum</p>
            <p>Veldtype:checkbox</p>
            <p>Veldtype: tekst</p>
            <p>VeldType: afbeelding</p>
            <p>toggle met text</p>
        </div>
    </div>

    <div class="scherm_container">
        <!-- header -->
        <div class="first_row_container">
            <div style="height:30%;display:flex;background-color: #f8fafc;  border-bottom:solid 2px #e3e9f0;flex-direction:row;">
            <p :style="kruimelpadStijl">{{ kruimeldpad }} </p>
            <div style="margin-left: auto;flex-direction: row;display:flex;align-self:center;justify-content: space-between;">
            <p style="">navigatiepijlen</p>
            <p style="margin-left:10px;">X</p>
            </div>
        </div>

        <div class="header_container">
            <img :scr="headerAfbeelding" alt="headerafbeelding" v-if="headerAfbeelding" >
            <h2 style="margin-top:1px;" >{{headerTitelCode  }}</h2>
        </div>    

    </div>
        <div class="eigenschappen_container">
                
            <!-- tabladen -->
            <div class="tabladen_acties_grid_item">
            tabladen
            </div>
            <!--velden  -->
            <div class="velden_grid_item">
                velden

            </div>
        </div>

    </div>


    <!-- 
        HRM > Medewerker (in dienst) > Floor van der Aar > Eigenschappen rooster
        Eigenschappen Rooster





     -->




    
   
  </template>
  
  <script lang="ts">
  import {ref} from "vue"
  import CustomElement from '../components/CustomElement.vue'
  export default {
    components: {
        CustomElement
        
      
    },
    setup() {
        const kruimeldpad = ref('');
        const kruimelpadStijl = ()=>{
            if(headerAfbeelding){
                return "align-self:center; margin-left:120px"
            } else {
                "align-self:center;margin-left:10px;"
            }

        }
        const headerAfbeelding = ref('');
        const handleFileUpload = (event: Event) => {
        const input = event.target as HTMLInputElement;
            if (input.files && input.files[0]) {
                const reader = new FileReader();
                reader.onload = () => {
                    headerAfbeelding.value = reader.result as string;
                };
                reader.readAsDataURL(input.files[0]);
            }
        };
      

        const headerTitelCode = ref('');


     
      return {
        kruimeldpad,
        kruimelpadStijl,
        headerAfbeelding,
        handleFileUpload,
        headerTitelCode
        ,
      
      };
    },

  };
  </script>
  
  <style>
body html{
    height:100vh;
    max-width: 100vw;
    margin:0;
    padding:0;
    display:inline;
  }  
#app{
    padding:0;
    margin:0;
}
header{
display:flex;
justify-content: center;
align-items: center;
width:100vw;
background-color: #492593;
height:5vh;
margin: auto;
color:white;

}

.title{
    font-size: 30px;
}

.grid_container_editor{
    display:grid;
    width:100vw;
    grid-template-columns:auto auto; 
    background-color:  #f8f9f9;
}

.grid_item_right, .grid_item_left{
    color:black; 
    background-color: white;
    margin: 30px;
    grid-template-columns:100%;
}

/* scherm */

.scherm_container{
    display:grid;
    margin:0 4% 4% 4%;
    box-shadow: 0px 0px 2px 2px black;
    height:100vh;
    width: 92vw;
    grid-template-columns:100%;
    grid-template-rows:15% 85%;
}

/* met kruimeldpad/navi/header */
.first_row_container{
    border:solid 2px #e3e9f0;
}

.tabladen_acties_grid_item{
    border-right:solid 2px #e3e9f0;
}

.eigenschappen_container{
    grid-template-columns:20% 80%; 
    display:grid;
    border:black;
}


.kruimelpad{
    display:flex;
    
}
.kruimelpad  p{
    display:block;
    font-size: 30px;
}

.header_container{
    display:flex;
}

.header_container img{
    margin-top:-20px;
    height:95px;
    width:90px;
    border:solid 1px black;
    margin-left: 10px;
    max-width: 500px; 
    max-height: 500px;

}










  </style>
  