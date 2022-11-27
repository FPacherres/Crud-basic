<template>
  <div class="container">
    <div class="header">
        <div>Nombre</div>
        <div>DNI</div>
        <div>Actiones</div>
    </div>
    <div class="list">
        <div class="item" v-for="(student, i) in students" 
        :key="i">
            <div>{{ student.name }}</div>
            <div>{{ student.dni }}</div>
            <div>
                <button @click="edit(i)">edit</button>
                <button @click="remove(i)">delete</button>
            </div>
        </div>
    </div>
    <div class="action">
        <button @click="add">Agregar</button>
    </div>
    <!-- <div class="A1 A">A1</div>
    <div class="A2 A">A2</div>
    <div class="A3 A">A3</div>
    <div class="A4 A">A4</div>
    <div class="A5 A">A5</div>
    <div class="A6 A">A6</div> -->
  </div>
</template>

<script>
// @ is an alias to /src

export default {
  name: 'list-custom',
  components: {},
  data() {
    return {
        students: []
    }
  },
  methods: {
    add() {
        this.students.push({
            name: "Marcos",
            dni: "934346457"
        })
    },
    remove(pos) {
        this.students.splice(pos,1)
    },
    edit(pos) {
        this.students.splice(pos,1, {name: "Fabian", dni: '1323423423'})
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
    background-color: rgb(214, 126, 17);
    display: grid;
    grid-template-columns: 2fr 1fr 200px;
}
.header div {
    display: flex;
    justify-content: center;
    align-items: center;
    border: 1px solid white;
}
.list {
    background-color: rgb(17, 214, 43);
}
.item {
    background-color: rgba(0, 0, 0, 0.123);
    display: grid;
    grid-template-columns: 2fr 1fr 200px;
}
.item div {
    border: 1px solid white;
}
.action {
    background-color: rgb(17, 165, 214);
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