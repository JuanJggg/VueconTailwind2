<script setup>
const mensajealerta= function(){
    alert("Buenas careburros")
}

const props = defineProps(
    {
        name: {
            type: String,
            default: "No tenemos nombre AY NO 😉"
        },
        correo: {
            type: String,
            default: "No tenemos correo AY NO 😂"
        },
        index:{
            type: Number
        }
    }
)

const borrarTarjeta= function(index){
    emit("borrarTarjeta",index)
}

const duplicarTarjeta= function(name,correo){
    emit("duplicarTarjeta",name,correo)
}

const emit = defineEmits(["borrarTarjeta","duplicarTarjeta"])
</script>


<template>
    <div class="bg-red-800 w-[250px] h-[200px] rounded-lg">
        <div class="flex justify-center items-center mt-24">
            <img src="https://cdn.pixabay.com/photo/2015/04/23/22/00/tree-736885_1280.jpg" class="w-[200px] mt-4 rounded-lg" @click="mensajealerta">
            <span class="bg-amber-500 w-6 rounded-md ml-1 mb-24 flex justify-center items-center cursor-pointer" @click="borrarTarjeta(props.index)">X</span>
            <span class="bg-amber-500 w-6 rounded-md ml-1 mb-24 flex justify-center items-center cursor-pointer" @click="duplicarTarjeta(props.name,props.correo)">ADD </span>
        </div>
        <div class="flex justify-center items-center">
            <div>
                <p>{{ props.name }}</p>
                <p>{{ props.correo }}</p>
            </div>
        </div>
    </div>
</template>