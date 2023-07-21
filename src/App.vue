<template>
    <div class="main-box">
        <div class="left box">
            <lists-comp :lists="lists" />
        </div>
        <div class="right box">
            <show-items :lists="lists" />
        </div>
    </div>
</template>
<script>
import ListsComp from "@/components/ListsComp";
import ShowItems from "@/components/ShowItems";

export default {
    components: {
        ListsComp, ShowItems
    },
    data() {
        return {
            lists: [
                {
                    id: 1, name: 'List 1', items: [
                        { id: 1, name: 'Item 1', quantity: 10, color: '#FF0000' },
                        { id: 2, name: 'Item 2', quantity: 16, color: '#FFFF00' },
                        { id: 3, name: 'Item 3', quantity: 40, color: '#008000' },
                        { id: 4, name: 'Item 4', quantity: 5, color: '#0000FF' }]
                },
                {
                    id: 2, name: 'List 2', items: [
                        { id: 1, name: 'Item 1', quantity: 25, color: '#808000' },
                        { id: 2, name: 'Item 2', quantity: 7, color: '#800080' },
                        { id: 3, name: 'Item 3', quantity: 15, color: '#808080' },
                        { id: 4, name: 'Item 4', quantity: 55, color: '#7FFF00' },
                        { id: 5, name: 'Item 5', quantity: 1, color: '#FFE4B5' },
                        { id: 6, name: 'Item 6', quantity: 23, color: '#DDA0DD' },
                        { id: 7, name: 'Item 7', quantity: 6, color: '#A0522D' },
                        { id: 8, name: 'Item 8', quantity: 12, color: '#800000' }]
                },
                {
                    id: 3, name: 'List 3', items: [
                        { id: 1, name: 'Item 1', quantity: 18, color: '#FFC0CB' },
                        { id: 2, name: 'Item 2', quantity: 46, color: '#EE82EE' },
                        { id: 3, name: 'Item 3', quantity: 11, color: '#FFE4C4' },
                        { id: 4, name: 'Item 4', quantity: 3, color: '#00FF00' }]
                },
                {
                    id: 4, name: 'List 4', items: [
                        { id: 1, name: 'Item 1', quantity: 29, color: '#000080' },
                        { id: 2, name: 'Item 2', quantity: 2, color: '#008080' },
                        { id: 3, name: 'Item 3', quantity: 65, color: '#FF1493' },
                        { id: 4, name: 'Item 4', quantity: 17, color: '#FFA500' }]
                },
                {
                    id: 5, name: 'List 5', items: [
                        { id: 1, name: 'Item 1', quantity: 33, color: '#F0E68C' },
                        { id: 2, name: 'Item 2', quantity: 27, color: '#8A2BE2' },
                        { id: 3, name: 'Item 3', quantity: 12, color: '#A52A2A' },
                        { id: 4, name: 'Item 4', quantity: 79, color: '#7FFFD4' }]
                }
            ]
        }
    }
}
</script>
<style>
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

.main-box {
    display: flex;
    justify-content: space-between;
    margin: 50px;
    padding: 15px;
    border: 3px solid black;
}

.box {
    padding: 15px;
    border: 2px solid black;
}

.left {
    width: 45%;
}

.right {
    width: 45%;
}
</style> 