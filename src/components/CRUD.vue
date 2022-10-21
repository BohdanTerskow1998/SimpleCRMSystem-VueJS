<script>
export default {
  data() {
    return {
      names: ['Terskow, Bohdan', 'Bandera, Stepan'],
      selected: '',
      first: '',
      last: ''
    }
  },
  watch: {
    selected(name) {
      ;[this.last, this.first] = name.split(', ');
    }
  },
  methods: {
    create() {
      const fullname = `${this.last}, ${this.first}`
      if(this.names.includes(fullname)) {
        alert("This name exists!")
      } else {
          return this.names.push(fullname)
      }
    },
    update() {
      const i = this.names.indexOf(this.selected)
      if(this.selected == 'Terskow, Bohdan') {
        alert("Error! You can't change admin name!")
      } else {
        this.names[i] = `${this.last}, ${this.first}`
      }
    },
    del() {
      const i = this.names.indexOf(this.selected)
      if(this.selected == 'Terskow, Bohdan') {
        alert("You can't to delete admin!")
      } else {
        this.names.splice(i, 1)
        this.selected = this.last = this.first = ''
      }
    }
  }
}
</script>

<template>
  <select size="5" v-model="selected">
    <option v-for="name in names.sort()" :key="name">{{name}}</option>
  </select><br />

  <div class="users">
    <label>Name: <input class="name" v-model="first" /></label><br />
    <label>Lastname: <input v-model="last" /></label>
  </div><br />

  <div class="buttons">
    <button @click="create">CREATE</button>
    <button @click="update">UPDATE</button>
    <button @click="del">DELETE</button>
  </div>
</template>