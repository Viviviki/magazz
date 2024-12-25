<template>
    <div class="good__card">
        <img class="card__image" :src="goodinfo.image" alt="good image">
        <p class="card__name">{{ goodinfo.title }}</p>
        <p class="card__price">${{ goodinfo.price }}</p>
        <p class="card__category">{{ goodinfo.category }}</p>
        <p class="card__rating">{{ goodinfo.rating.rate }}</p>
        <RouterLink class="card__more" :to="'/good' + goodinfo.id">Подробнее</RouterLink>
    </div>
</template>

<script>
export default {
    props: {
        goodinfo: Object
    }
}
</script>

<style>
.good__card {
    display: flex;
    flex-direction: column;
    align-items: center;
    width: 250px;
    height: 350px;
    box-shadow: 2px 3px 5px 2px #c1a90d;
    border-radius: 10px;
    gap: 8px;
    font-size: 14px;
}

.card__image {
    width: 250px;
    height: 175px;
    object-fit: contain;
    object-position: center;
}

.card__more {
    display: flex;
    align-items: center;
    justify-content: center;
    width: 100px;
    height: 40px;
    text-decoration: none;
    background-color: #c1a90d;
    border-radius: 20px;
    color: #FFF;
}
</style>