<template>
    <div class="main_container">
        <div class="header">
            <h1 class="header_title">Invictus</h1>
            <p class="header_text">By William Ernest Henley</p>
        </div>
        <div class="components">
            <div class="control_container">
                <ControlElement class="item_control" v-for="(elem, index) in textData" :key="index"
                                :quatrainData="elem" @eventButtonClick="receivingClickButton"/>
            </div>
            <div class="poem_container">
                <div v-for="(elem, index) in textData" :key="index">
                    <PoemText v-if="!elem.hide" class="item_poem" :quatrain="elem.text"/>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    import {ref} from 'vue'
    import ControlElement from "../components/ControlElement.vue";
    import PoemText from "../components/PoemText.vue";
    import {v4 as uuidv4} from 'uuid'


    export default {
        name: "HomePage",
        components: {PoemText, ControlElement},
        setup() {
            const textData = ref([
                {
                    id: uuidv4(),
                    text: 'Out of the night that covers me,\n' +
                        '      Black as the pit from pole to pole,\n' +
                        'I thank whatever gods may be\n' +
                        '      For my unconquerable soul.',
                    hide: false
                },
                {
                    id: uuidv4(),
                    text: 'In the fell clutch of circumstance\n' +
                        '      I have not winced nor cried aloud.\n' +
                        'Under the bludgeonings of chance\n' +
                        '      My head is bloody, but unbowed.',
                    hide: false
                },
                {
                    id: uuidv4(),
                    text: 'Beyond this place of wrath and tears\n' +
                        '      Looms but the Horror of the shade,\n' +
                        'And yet the menace of the years\n' +
                        '      Finds and shall find me unafraid.',
                    hide: false
                },
                {
                    id: uuidv4(),
                    text: 'It matters not how strait the gate,\n' +
                        '      How charged with punishments the scroll,\n' +
                        'I am the master of my fate,\n' +
                        '      I am the captain of my soul.',
                    hide: false
                }
            ])
            const receivingClickButton = (quatrainId) => {
                const quatrain = textData.value.find((elem) => elem.id === quatrainId)
                if (!quatrain.hide) {
                    const filter = textData.value.filter((elem) => elem.hide)
                    if (filter.length === textData.value.length - 1) {
                        return;
                    }
                }
                textData.value = textData.value.map((elem) => {
                    if (elem.id === quatrainId) {
                        elem.hide = !elem.hide
                        return elem
                    }
                    return elem
                })
            }
            return {
                textData,
                receivingClickButton
            }
        }
    }
</script>

<style scoped>
    .header {
        display: flex;
        justify-content: center;
        padding-left: 21.354vw;
    }

    .header_title {
        margin: 0;
        padding-top: 12px;
        font-size: clamp(26px, 3.333vw, 64px);
        white-space: pre;
        font-weight: normal;
    }

    .header_text {
        margin: 0;
        display: flex;
        align-items: end;
        padding-left: 5.99vw;
        font-size: clamp(18px, 1.667vw, 36px);
    }

    .components {
        display: flex;
        padding-top: 15px;
        padding-left: 12.969vw;
    }

    .control_container {
        display: flex;
        padding-top: 7px;
    }

    .item_control {
        margin-right: 35px;
    }

    .poem_container {
        padding-left: 5px;
    }

    .item_poem {
        line-height: 50px;
        margin-bottom: 30px;
    }

    @media (max-width: 1440px) {
        .header {
            padding-left: 82px;
        }

        .components {
            display: block;
            padding-top: 15px;
            padding-left: 12.969vw;
        }

        .control_container {
            justify-content: center;
            padding-top: 0;
        }

        .poem_container {
            display: flex;
            flex-direction: column;
            align-items: center;
            padding-left: 0;
            padding-top: 15px;
        }

        .item_poem {
            width: 392px;
            line-height: normal;
            margin-bottom: 10px;
        }
    }

    @media (min-width: 702px) {

    }

    @media (min-width: 702px) and (max-width: 1919px) {
        .item_poem {
            width: 551px;
        }
    }

    @media (min-width: 1930px) {
        .components {

            padding-left: 20vw;
        }
    }
</style>
