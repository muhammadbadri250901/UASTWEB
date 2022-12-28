<script>
export default {
  data() {
    return {
      names: ['001, ucup', '002, samsul', '003, jumingten'],
      selected: '',
      prefix: '',
      nama: '',
      nim: ''
    }
  },
  computed: {
    filteredNames() {
      return this.names.filter((n) =>
        n.toLowerCase().startsWith(this.prefix.toLowerCase())
      )
    }
  },
  watch: {
    selected(ID) {
      ;[this.nim, this.nama] = ID.split(', ')
    }
  },
  methods: {
    create() {
      if (this.hasValidInput()) {
        const fullName = `${this.nim}, ${this.nama}`
        if (!this.names.includes(fullName)) {
          this.names.push(fullName)
          this.nama = this.nim = ''
        }
      }
    },
    update() {
      if (this.hasValidInput() && this.selected) {
        const i = this.names.indexOf(this.selected)
        this.names[i] = this.selected = `${this.nim}, ${this.nama}`
      }
    },
    del() {
      if (this.selected) {
        const i = this.names.indexOf(this.selected)
        this.names.splice(i, 1)
        this.selected = this.nama = this.nim = ''
      }
    },
    hasValidInput() {
      return this.nama.trim() && this.nim.trim()
    }
  }
}
</script>

<template>
  <div><input v-model="prefix" placeholder="Filter prefix"></div>

  <select size="5" v-model="selected">
    <option v-for="ID in filteredNames" :key="ID">{{ ID }}</option>
  </select>

  <label>Nama<input v-model="nama"></label>
  <label>Nim: <input v-model="nim"></label>

  <div class="buttons">
    <button @click="create">Create</button>
    <button @click="update">Update</button>
    <button @click="del">Delete</button>
  </div>
</template>
<style>
#AboutView{
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

* {
  font-size: inherit;
}

input {
  display: block;
  margin-bottom: 10px;
}

select {
  float: left;
  margin: 0 1em 1em 0;
  width: 14em;
}

.buttons {
  clear: both;
}

button + button {
  margin-left: 5px;
}
</style>
