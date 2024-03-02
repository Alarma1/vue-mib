<template>
    <div>
        <button class="btn" @click="elementClick(quatrainData.id)"
                :class="{'btn_active':quatrainData.hide}"></button>
    </div>
</template>

<script>

    export default {
        name: "ControlElement",
        props: ['quatrainData'],
        setup(props, {emit}) {
            const elementClick = (id) => {
                emit('eventButtonClick', id);
            }
            return {
                elementClick
            }
        }
    }

</script>

<style scoped>
    .btn {
        width: 36px;
        height: 36px;
        border: 3px solid black;
        background-color: black;
    }

    .btn_active {
        background-color: white;
    }
</style>
