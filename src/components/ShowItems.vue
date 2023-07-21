<template>
    <div class="show-items" v-for="list in lists" :key="list.id">
        <p>{{ list.name }}</p>
        <div class="items-block">
        </div>
    </div>
</template>
<script>
export default {
    props: {
        lists: {
            type: Array,
            required: true
        }
    },
    methods: {
        checkboxList() {
            const id = event.target.dataset.id - 1;
            const lists = document.querySelectorAll('.list');
            const items = lists[id].querySelectorAll('.checkbox-item');
            if (event.target.checked === true) {
                items.forEach(e => {
                    e.checked = true;
                })
            } else {
                items.forEach(e => {
                    e.checked = false;
                })
            }
        },
        indeterminate() {
            const lists = document.querySelectorAll('.list');
            for (let i = 0; i < lists.length; i++) {
                const checkItems = lists[i].querySelectorAll('.checkbox-item');
                let result = 0;
                let done = 0;
                for (let j = 0; j < checkItems.length; j++) {
                    if (checkItems[j].checked === true) {
                        result = 1;
                    }
                }
                if (result === 1) {
                    lists[i].querySelector('.checkbox-list').indeterminate = true;
                } else {
                    lists[i].querySelector('.checkbox-list').indeterminate = false;
                    lists[i].querySelector('.checkbox-list').checked = false;
                }
                for (let k = 0; k < checkItems.length; k++) {
                    if (checkItems[k].checked === false) {
                        done = 1;
                    }
                }
                if (done === 0) {
                    lists[i].querySelector('.checkbox-list').indeterminate = false;
                    lists[i].querySelector('.checkbox-list').checked = true;
                }
            }
        }
    }
}
</script>
<style>
.show-items {
    border: 2px solid black;
    margin-bottom: 10px;
    padding: 5px;
}
</style>