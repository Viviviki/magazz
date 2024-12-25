<template>
    <div class="goods__grid">
        <p v-if="!categories" class="loader">Загрузка...</p>
        <div v-else class="goods_grid_filters">
            <button class="filters__button button" @click="changeCatAll()">All</button>
            <button class="filters__button button" @click="changeCat(cat)" v-for="(cat, key) in categories" :key="key">{{ cat }}</button>
        </div>
        <p v-if="!goods" class="loader">Загрузка...</p>
        <div v-else class="grid">
            <GoodsCard v-for="(good, key) in goods.slice(startSlice, startSlice + 10)" :key="key" :goodinfo="good" />
        </div>
        <p v-if="!goods" class="loader">Загрузка...</p>
        <div v-else class="goods_grid_paging">
            <button class="paging__button button" @click="startSlice -= 10">{{ '<<' }}</button>
            <div class="paging__pages">
                <p class="paging__page" v-for="(page, key) in Math.floor(goods.length / 10)" :key="key">{{ page }}</p>
            </div>
            <button class="paging__button button" @click="startSlice += 10">{{ '>>' }}</button>
        </div>
    </div>
</template>

<script>
import GoodsCard from './GoodsCard.vue';

export default {
    components: {
        GoodsCard
    },
    data() {
        return {
            goods: null,
            categories: null,
            startSlice: 0
        }
    },
    methods: {
        changeCat(cat) {
            fetch(`https://fakestoreapi.com/products/category/${cat}`)
            .then(resp => resp.json())
            .then(json => {
                this.goods = json;
            });
        },
        changeCatAll() {
            fetch('https://fakestoreapi.com/products')
            .then(resp => resp.json())
            .then(json => {
                this.goods = json;
            });
        }
    },
    mounted() {
        fetch('https://fakestoreapi.com/products/categories')
        .then(resp => resp.json())
        .then(json => {
            this.categories = json;
        });
        fetch('https://fakestoreapi.com/products')
        .then(resp => resp.json())
        .then(json => {
            this.goods = json;
        });
    }
}
</script>

<style>
.goods__grid {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 15px;
    width: 1140px;
    margin: 0 auto;
}

.filters__button.button {
    height: 30px;
    border-radius: 30px;
    border: none;
    padding: 0 10px;
    cursor: pointer;
}

.grid {
    display: grid;
    justify-content: center;
    align-items: center;
    align-content: center;
    width: 1140px;
    grid-template-columns: repeat(auto-fill, 250px);
    gap: 20px;
}

.goods_grid_paging {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 20px;
}

.paging__pages {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 15px;
}

.paging__button.button {
    display: flex;
    align-items: center;
    justify-content: center;
    width: 100px;
    height: 40px;
    text-decoration: none;
    background-color: #c1a90d;
    border-radius: 20px;
    border: none;
    color: #FFF;
    cursor: pointer;
}
</style>