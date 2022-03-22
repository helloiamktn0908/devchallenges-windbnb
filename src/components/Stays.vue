<template>
  <div class="stays__wrapper">
    <div class="stays__header">
      <span class="stays__header_title">Stays in Finland</span>
      <span class="stays__header_count">12 + stays</span>
    </div>
    <div class="stays__list">
      <div v-for="stay in stays" :key="stay.id">
        <img :src="stay.image" class="stays__stay_image" />
        <div class="stays__stay_status">
          <div>
            <span v-if="stay.isSuper" class="stays__stay_tag">SUPER HOST</span>
            <span class="stays__stay_category">{{ stay.category }}</span>
          </div>
          <div class="stays__stay_rateWrapper">
            <span class="material-icons stays__stay_star">star</span>
            <span class="stays__stay_rate">{{ stay.rate }}</span>
          </div>
        </div>
        <p class="stays__stay_name">{{ stay.name }}</p>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

interface Stays {
  id: number;
  name: string;
  image: string;
  category: string;
  isSuper: boolean;
  rate: string;
}

export default defineComponent({
  data() {
    return {
      stays: [
        {
          id: 0,
          name: 'Styelist apartment in center of the city',
          image: '../../public/room1.jpeg',
          category: 'Entire apartment . 2 beds',
          isSuper: true,
          rate: '4.40',
        },
        {
          id: 1,
          name: 'Cozy, peaceful and private room with...',
          image: '../../public/room2.jpeg',
          category: 'Private room',
          isSuper: false,
          rate: '4.25',
        },
        {
          id: 2,
          name: 'Mordern House in a remote area',
          image: '../../public/room3.jpeg',
          category: 'Entire house',
          isSuper: false,
          rate: '4.96',
        },
        {
          id: 3,
          name: 'Entire apartment . 2 beds',
          image: '../../public/room4.jpeg',
          category: 'Entire apartment . 2 beds',
          isSuper: true,
          rate: '4.85',
        },
        {
          id: 4,
          name: 'Modern apartment close to nature',
          image: '../../public/room5.jpeg',
          category: 'Private room',
          isSuper: false,
          rate: '4.54',
        },
        {
          id: 5,
          name: 'House in a remote area',
          image: '../../public/room6.jpeg',
          category: 'Entire house',
          isSuper: false,
          rate: '4.64',
        },
      ] as Stays[],
    };
  },
});
</script>

<style>
.stays__wrapper {
  padding: 2rem 6rem;
  font-family: 'Montserrat', Avenir, Helvetica, Arial, sans-serif;
  min-height: 100vh;
}

.stays__header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 32px;
}

.stays__header_title {
  font-size: 24px;
  font-weight: 700;
}

.stays__header_count {
  font-size: 14px;
  font-weight: 500;
}

.stays__list {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
}

.stays__stay_image {
  width: 395px;
  height: 269px;
  border-radius: 24px;
  margin-bottom: 15px;
}

.stays__stay_status {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.stays__stay_tag {
  font-size: 12px;
  font-weight: 700;
  padding: 6px 10px;
  border: 1px solid #4f4f4f;
  border-radius: 12px;
  margin-right: 10px;
}

.stays__stay_category {
  font-size: 14px;
  color: #828282;
  font-weight: 500;
}

.stays__stay_rateWrapper {
  display: flex;
  align-items: center;
}

.stays__stay_star {
  color: #eb5757;
  font-size: 20px;
}

.stays__stay_rate {
  font-size: 14px;
  font-weight: 500;
  color: #4f4f4f;
}

.stays__stay_name {
  font-size: 16px;
  font-weight: 600;
  margin-bottom: 50px;
  text-align: left;
}
</style>
