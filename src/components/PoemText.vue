<template>
    <div>
        <p class="item_text" v-for="(text, index) in modifiedQuatrain" :key="index">{{ text }}</p>
    </div>
</template>

<script>
    import {ref, computed} from 'vue'

    export default {
        name: "PoemText",
        props: ['quatrain'],
        setup(props) {
            const modifiedQuatrain = computed(() => props.quatrain.split("\n"))
            const quatrainView = ref(true)
            return {
                modifiedQuatrain,
                quatrainView
            }
        }
    }
</script>

<style lang="scss" scoped>
    .item_text {
        margin-top: 0;
        margin-right: 0;
        margin-bottom: 0;
    }

    .item_text:nth-child(even) {
        padding-left: 77px
    }

    @media (max-width: 467px) {
        .item_text {
            font-size: 14px;
        }
    }

    @media (min-width: 702px) and (max-width: 1920px) {
        .item_text {
            font-size: 22px;
        }
    }

    @media (min-width: 1920px) {
        .item_text {
            font-size: 40px;
        }
    }

    @media (min-width: 1930px) {
        .item_text {
            font-size: 50px;
        }
    }
</style>
