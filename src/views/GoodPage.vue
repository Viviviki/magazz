<template>
  <div class="good__page">
      <p v-if="!goodInfo">Загрузка...</p>
      <div v-else class="good__desc">
          <div class="good__description">
              <p class="description">Описание: {{ goodInfo.description }}</p>
              <div class="good__rating">
                  <p class="rating__rate">Рейтинг: {{ goodInfo.rating.rate }}</p>
                  <p class="rating__count">Кол-во отзывов: {{ goodInfo.rating.count }}</p>
              </div>
          </div>
          <img class="good__image" :src="goodInfo.image" alt="good image">
      </div>
  </div>
</template>

<script>
export default {
  data() {
      return {
          goodInfo: null
      }
  },
  mounted() {
      fetch(`https://fakestoreapi.com/products/${this.$route.params.id}`)
          .then(resp => resp.json())
          .then(json => {
              this.goodInfo = json;
          });
  }
}
</script>

<style>
.good__image {
  width: 30%;
  height: 100%;
}

.good__desc {
  width: 1140px;
  display: flex;
  justify-content: space-between;
  margin: 0 auto;
}

.good__description {
  width: 40%;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  background-color: #c1a90d;
  color: #FFF;
  border-radius: 30px;
  padding: 15px;
  font-size: 24px;
  box-shadow: 3px 3px 5px 5px #747474;
}
</style>