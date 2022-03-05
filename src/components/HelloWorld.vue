<template>
    <div class="estadistica">      

            <div class="botones">
              <p> Agregar </p>
              <button class="btn btn-success" @click="agregar"> Agregar </button>
              <p> Eliminar </p>
              <button class="btn btn-danger" @click="eliminar"> Eliminar </button>
            </div>

            <div v-for="(suc) in sucursales" :key="suc">          
               
              <div class="border border-4">
                {{suc.name}}
                <p>
                  <button :class="{conectado: suc.stateconection == true, desconectado: suc.stateconection == false}" disabled>Status</button>                    
                </p>
                
              </div>
            </div>
            <div>
              
            </div>
    </div>
</template>

<script>
    export default {

        data() {
            return {
                sucursales : [
                  {id:1, name:"San Pablo Uno", stateconection:true},
                  {id:2, name:"San Pablo Dos", stateconection:true},
                  {id:3, name:"Correo Uno", stateconection:false},
                  {id:4, name:"Correo Dos", stateconection:true},
                ]
            }
        },


    }

</script>



<style scoped>
    .estadistica{
        padding-top: 20px;
      display: flex;
      justify-content: space-a;
      text-align: center;
      flex-wrap: wrap;
      margin: 20px;     
      padding: 10px;
      width: 100%;
      height: 100%;
      background-color: #f2f2f2;
    }

    .botones{
      display: flex;
      justify-content: space-around;
      text-align: center;
      flex-wrap: wrap;
      margin: 20px;     
      padding: 10px;
      width: 100%;
      height: 100%;
      background-color: #f2f2f2;
    }


    .border{
      border: 1px solid #ccc;
      border-radius: 4px;
      background-color: #f8f8f8;
      width: 300px;
      height: 100px;
      margin-top: 10px;

    }

    .desconectado{
      border-radius: 4px;
      margin-top: 20px;
        background-color: #ff0000;
    }

    .conectado{
      border-radius: 4px;
      margin-top: 20px;
        background-color: #00ff00;
    }

</style>