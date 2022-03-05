<template>
    <div class="estadistica">      

            <div class="botones">
              <form v-on:submit="agregar">
                <input v-model="inputName" type="text" placeholder="Nombre" required>
                <input v-model="inputConnect" type="text" placeholder="True/False " required>
                <input type="submit" value="Agregar" class="btn btn-success">                    
              </form>
              <div class="botonRojo">
              <button class="btn btn-danger" @click="eliminar"> Eliminar </button>  
              </div>            
              
              
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

        methods: {
            agregar(e){
              e.preventDefault();
              
              console.log("Agregar");
              // Convertir el estado de conexion a boolean
              this.sucursales.push({id:this.sucursales.length+1, name:this.inputName, stateconection:this.inputConnect == "true"})
              
            },
            eliminar(e){
              e.preventDefault();
              //this.sucursales.pop()
              console.log("Eliminar");
              this.sucursales.pop()
              if(this.sucursales.length == 0){
                alert("No hay mas sucursales")
              }
            },

            cambiarStateconection(){
              this.sucursales.stateconection = !this.sucursales.stateconection
              console.log(this.sucursales.stateconection)
            }

        },
        created(){
          // Si me lo detecta en la consola, pero no hace los cambios
          // Lo mandé ahorita para que se vea el avance, aun asi le seguire viendo cual es el error
          let funcionInterval;
          setInterval(this.cambiarStateconection,2000);
        } 

    }

</script>



<style scoped>
    .estadistica{
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

  form{
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
    width: 100%;
    height: 100%;  
  }

  form > input{
    width: 50%;
    height: 50px;
    margin: 10px;
    border-radius: 5px;
    border: 1px solid #ccc;
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

  .botonRojo{
    display: flex;
    justify-content: flex-end;
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