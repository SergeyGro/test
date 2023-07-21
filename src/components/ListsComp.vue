<template>
    <details class="list" v-for="list in lists" :key="list.id">
        <summary><input class="checkbox-list show" type="checkbox" @change="checkboxList" :data-id="list.id">{{ list.name }}
        </summary>
        <div class="item" v-for="item in list.items" :key="item.id">
            <div class="item-name">
                <input class="checkbox-item show" type="checkbox" @change="indeterminate" @click="renderItems"
                    :data-id="item.id">
                {{ item.name }}
            </div>
            <div class="item-data">
                <input class="input-quantity" type="number" :value="item.quantity">
                <input class="color-input" type="color" :value="item.color">
            </div>
        </div>
    </details>
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
        },
        renderItems(event) {
            const index = event.target.dataset.id - 1;
            const itemsBlock = document.querySelectorAll('.items-block');
            if (event.target.classList.contains('checkbox-list')) {
                this.lists[index].items.forEach(e => {
                    const elements = document.createElement('div');
                    elements.classList.add('elements');
                    for (let j = 0; j < e.quantity; j++) {
                        const item = document.createElement('div');
                        item.classList.add('show-item');
                        item.style.backgroundColor = `${e.color}`;
                        elements.append(item);
                    }
                    itemsBlock[index].append(elements);
                })
            } else {
                // const groupEl = this.lists[index].items.filter(e => {
                //     return e.id == event.target.dataset.id;
                // })
                console.log(event.target)
                // const elements = document.createElement('div');
                // elements.classList.add('elements');
                // for (let j = 0; j < groupEl.quantity; j++) {
                //     const item = document.createElement('div');
                //     item.classList.add('show-item');
                //     item.style.backgroundColor = `${groupEl.color}`;
                //     elements.append(item);
                // }
                // itemsBlock[index].append(elements);
            }
        },
        deleteItems(event) {
            const index = event.target.dataset.id - 1;
            const itemsBlock = document.querySelectorAll('.items-block');
            itemsBlock[index].innerHTML = '';
        }
    },
    mounted() {
        const inputs = document.querySelectorAll('.show');
        for (let i = 0; i < inputs.length; i++) {
            inputs[i].addEventListener('change', () => {
                if (inputs[i].checked === true) {
                    this.renderItems(event);
                } else {
                    this.deleteItems(event);
                }

            })
        }
    }
}
</script>
<style>
.list {
    margin-bottom: 10px;
}

.item {
    display: flex;
    justify-content: space-between;
    margin-top: 10px;
}

.item-name {
    display: flex;
    margin-left: 20px;
}

input {
    margin-right: 7px;
}

.item-data {
    display: flex;
}

.input-quantity {
    max-width: 40px;
}

.color-input {
    border: none;
    width: 20px;
    height: 20px;

}

.items-block {
    display: flex;
    flex-direction: column;
}

.elements {
    display: flex;
    flex-wrap: wrap;
    margin-bottom: 10px;
}

.show-item {
    width: 10px;
    height: 10px;
    margin: 2px 2px 0 0;
}
</style>