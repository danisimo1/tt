<template>
  <form v-if="visible" @submit.prevent>
    <input type="text" placeholder="Имя" v-model="name"><br><br>
    <input type="text" placeholder="Фамилия" v-model="secName"><br><br>
    <input type="text" placeholder="Отчество" v-model="thName"><br><br>
    <input type="text" placeholder="Должность" v-model="job"><br><br>
    <input type="checkbox" value="Трудовая книжка сдана">Трудовая книжка сдана<br><br>
    <input type="text" placeholder="Оклад"><br><br>
    <input type="date"/><br><br>
    <input type="radio" v-model="type" name="question">
    <label>Полная ставка</label>
    <br>
    <input type="radio" v-model="type" name="question">
    <label>Половина ставки</label><br><br>
    <button @click="newEmp">Создать</button><br><br>
  </form>
  <button @click="visible = !visible">Добавить сотрудника</button>
  <br>
  <br>
  <ol>
    <li v-for="employe in employees" v-bind:key="employe.id">
      {{employe.secondName + ' ' + employe.firstName + ' ' + employe.thirdName + ' - ' + employe.position}} 
      <button @click="deleteEmp">Удалить</button>
    </li>
  </ol>
</template>

<script>

export default {
  name: 'App',
  data(){
    return {
      employees: [
        {firstName: 'Альберт', secondName: 'Алмазов', thirdName: 'Альбертович', position: 'frontend-разработчик'},
        {firstName: 'Иван', secondName: 'Иванов', thirdName: 'Иванович', position: 'backend-разработчик'},
        {firstName: 'Дильшот', secondName: 'Ахматов', thirdName: 'Александрович', position: 'devOps-инженер'}
      ],
      visible: false,
      type: '',
      name: '',
      secName: '',
      thName: '',
      job: ''
    }
  },
  methods: {
    newEmp(){
      const newEmpl = {firstName: this.name, secondName: this.secName, thirdName: this.thName, position: this.job}
      this.employees.push(newEmpl)
      this.name = ''
      this.secName = ''
      this.thName = ''
      this.job = ''
    },
    deleteEmp(employe){
      this.employees = this.employees.filter(p => p.id !== employe.id)
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}

form{
  border: 1px solid black;
  width: 500px;
  padding: 15px;
}
</style>
