<template>
    <div class="container">
        <div class="formulario">
            <label for="Nombre">Nombre: </label>
            <input type="text" v-model="nombre">
            <label for="Apellido">Apellido: </label>
            <input type="text" v-model="apellido">
            <button class="blue-btn" @click="agregarUsuario">Confirmar</button>
        </div>
        <div class="lista">
            <ul v-for="usuario in usuarios" :key="usuario.id"> 
                {{ usuario }}
                <input type="text" placeholder="Nuevo Nombre" model="nuevoNombre">
                <input type="text" placeholder="Nuevo Apellido" v-model="nuevoApellido">
                <button class="blue-btn" @click="modificarUsuario(usuario.id)">Modificar</button>
                <button class="red-btn" @click="eliminarUsuario(usuario.id)">Eliminar</button>
            </ul>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'formComponent',
        data () {
            return {
                nombre: '',
                apellido: '',
                nuevoNombre: '',
                nuevoApellido: '',
                usuarios: []

            }
        },
        methods: {
            agregarUsuario() {
                if (this.apellido && this.nombre.trim() !== '') {
                    this.usuarios.push(this.nombre+' '+this.apellido);
                } else {
                    alert('Rellena todos los campos!');
                }
            },
            modificarUsuario(index) {
                this.usuarios[index] = this.nuevoNombre+' '+this.nuevoApellido;
            },
            eliminarUsuario(index) {
                this.usuarios.pop(index)
            }
        }
    }
</script>

<style>
    * {
        font-family: Arial, Helvetica, sans-serif;
        padding: 0;
        margin: 0;
    }
    .container {
        width: 48%;
        margin-top: 180px;
        margin-left: 400px;
        align-items: center
    }
    .formulario {
        display: flex;
        flex-direction: column;
    }
    .lista {
        margin-left: 80px;
    }
    .red-btn {
        padding: 12px;
        background-color: rgb(255, 59, 59);
        border: none;
        border-radius: 10px;
        color: white;
        margin: 10px;
    }
    .blue-btn {
        padding: 12px;
        background-color: rgb(59, 164, 255);
        border: none;
        border-radius: 10px;
        color: white;
        margin: 10px;
    }
    .red-btn:hover {
        background-color: rgb(222, 48, 48);
    }
    .blue-btn:hover {
        background-color: rgb(30, 127, 212);
    }
    input {
        padding: 12px;
        background-color: #f3f3f3;
        border: none;
        border-radius: 10px;
        margin-bottom: 10px;
        margin-right: 10px;
    }
</style>