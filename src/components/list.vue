<template>
  <div class="container">
    <div class="header">
        <div>Nombres</div>
        <div>Apellidos</div>
        <div>DNI</div>
        <div>Genero</div>
        <div>Actiones</div>
    </div>
    <div class="list">
        <div class="item" v-for="(student, i) in students" 
        :key="i">
            <div>{{ student.name }}</div>
            <div>{{student.surname}}</div>
            <div>{{ student.dni }}</div>
            <div>{{ student.genero }}</div>
            <div>
                <button @click="showModalEdit(i)">edit</button>
                <button @click="remove(i)">delete</button>
            </div>
        </div>
    </div>
    <div class="action">
        <button @click="showModal = true">Agregar</button>
    </div>
    <!-- <div class="A1 A">A1</div>
    <div class="A2 A">A2</div>
    <div class="A3 A">A3</div>
    <div class="A4 A">A4</div>
    <div class="A5 A">A5</div>
    <div class="A6 A">A6</div> -->
    <div class="modal" v-if="showModal">
        <label>Nombres</label>
        <input v-model="Name" type="text" placeholder="Nombre">
        <label>Apellidos</label>
        <input v-model="Surname" type="text" placeholder="Apellido">
        <label>Dni</label>
        <input v-model="Dni" type="text" placeholder="Dni">
        <label>Genero</label>
        <input v-model="Genero" type="text" placeholder="Genero">
        <button @click="action">Guardar</button>
        <button @click="showModal = false, pos=null">Cancelar</button>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src

export default {
  name: 'list-custom',
  components: {},
  data() {
    return {
        students: [],
        showModal: false,
        Name: '',
        Surname: '',
        Dni: '',
        Genero: '',
        pos: null
    }
  },
  //Agregar validacion y luego pushear, no editar si no estan 
  //los datos llenos, dni
  //hombre y mujer nuevo campo. 
  //Nombres y Apellidos solo texto. no numeros
  methods: {
    add() {
        //if(this.Name && this.Surname && this.Dni){
        //    return true;
        //}
        this.students.push({
            name: this.Name,
            surname: this.Surname,
            dni: this.Dni,
            genero: this.Genero
        })
        //if (!this.Name) {
        //this.errors.push('El nombre es obligatorio.');
        //}
        //if (!this.Surname) {
        //this.errors.push('El apellido es obligatorio.');
        //}
        //if (!this.Dni) {
        //this.errors.push('El DNI es obligatorio.');
        //}
                
        this.showModal = false
        this.clearModal()
    },
    action() {
        this.pos===null ? this.add() : this.edit()
    },
    clearModal() {
        this.Name = ''
        this.Surname = ''
        this.Dni = ''
        this.Genero = ''
        this.pos = null
    },
    remove(pos) {
        this.students.splice(pos,1)
    },
    edit(pos) {        
        this.students.splice(pos,1, {name: this.Name, surname: this.Surname, dni: this.Dni, genero: this.Genero})
        this.showModal = false
        this.clearModal()
    },
    showModalEdit(pos) {
        this.showModal = true
        this.pos = pos
    }
  }
}
</script>

<style scoped>
.container {
    color: white;
    height: 80%;
    width: 80%;
    background: blue;
    display: grid;
    grid-template-rows: 40px 1fr 40px ;
    /* display: grid;
    grid-template-areas: 
        'A1 A1 A2' 
        'A3 A4 A5'
        'A3 A6 A5'; */
}
.header {
    background-color: #36C9C6;
    display: grid;
    grid-template-columns: 1fr 1fr 1fr  1fr 100px;
}
.header div {
    display: flex;
    justify-content: center;
    align-items: center;
    border: 1px solid white;
}
.list {
    background-color: #E6EBE0;
    border: 1px solid #a3a5a1;
}
.item {
    background-color: rgba(0, 0, 0, 0.123);
    display: grid;
    grid-template-columns: 1fr 1fr 1fr 1fr 100px;
}
.item div {
    border: 1px solid white;
}
.action {
    background-color: rgb(17, 165, 214);
}
.modal {
    position: absolute;
    width: 200px;
    height: 200px;
    background-color: black;
    top: 0;
    bottom: 0;
    left: 0;
    right: 0;
    margin: auto;
}
/* .A {
    font-size: 20px;
    display: flex;
    justify-content: center;
    align-items: center;
}
.A1 {
    grid-area: A1;
    background-color: aqua;
}
.A2 {
    grid-area: A2;
    background-color: rgb(55, 255, 0);
}
.A3 {
    grid-area: A3;
    background-color: rgb(238, 255, 0);
}
.A4 {
    grid-area: A4;
    background-color: rgb(255, 38, 0);
}
.A5 {
    grid-area: A5;
    background-color: rgb(255, 0, 174);
}
.A6 {
    grid-area: A6;
    background-color: rgb(0, 0, 0);
} */

</style>