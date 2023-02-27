<template>
    <button 
    class= "btn"
    :style= "{ background: color}"
    @click= "$emit('toggle-add-task')">
        {{ text }}
    </button>
</template>

<script>
export default {
    name: 'Button',
    props: {
        text: String,
        color: String
    }
}
</script>
