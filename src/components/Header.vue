<template>
  <header>
    <div class="header" @click="clickHeader">
      <h1>
        <img alt="Vue logo" src="../../public/logo.svg" />
      </h1>
      <div class="header__search">
        <span class="header__location">{{ selectedLocation }}</span>
        <span class="header__guests">Add guests</span>
        <div class="header__searchButton">
          <span class="material-icons header__searchIcon">search</span>
        </div>
      </div>
    </div>
    <keep-alive>
      <Drawer
        v-if="isHeaderClicked"
        @search="search"
        @selectedLocationName="setLocation"
        :locations="locations"
    /></keep-alive>
  </header>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import Drawer from './Drawer.vue';

export interface Location {
  id: number;
  name: string;
}

export default defineComponent({
  components: {
    Drawer,
  },
  data() {
    return {
      locations: [
        { id: 0, name: 'Helsinki, Finland' },
        { id: 1, name: 'Turku, Finland' },
        { id: 2, name: 'Oulu, Finland' },
        { id: 3, name: 'Vasa, Finland' },
      ] as Location[],
      isClicked: {
        location: false,
        guests: false,
      },
      selectedLocation: 'Helsinki, Finland',
      adultsCount: 0,
      childrenCount: 0,
      isHeaderClicked: false,
    };
  },
  computed: {
    totalGuests(): string {
      return `${this.adultsCount + this.childrenCount} guests`;
    },
  },
  methods: {
    clickHeader() {
      this.isHeaderClicked = true;
    },
    setLocation(locationName: string) {
      this.selectedLocation = locationName;
    },
    clickGuests() {
      this.isClicked.location = false;
      this.isClicked.guests = true;
    },
    adultsCountDown() {
      if (this.adultsCount > 0) {
        this.adultsCount--;
      }
    },
    adultsCountUp() {
      this.adultsCount++;
    },
    childrenCountDown() {
      if (this.childrenCount > 0) {
        this.childrenCount--;
      }
    },
    childrenCountUp() {
      this.childrenCount++;
    },
    search() {
      this.isHeaderClicked = false;
    },
  },
});
</script>

<style>
header {
  position: relative;
}

.header {
  display: flex;
  justify-content: space-between;
  padding: 2rem 6rem;
}

h1 {
  margin: 0;
}

.header__search {
  height: 55px;
  width: 297px;
  border-radius: 16px;
  box-shadow: 0px 1px 6px rgba(0, 0, 0, 0.1);
  display: flex;
  align-items: center;
}

.header__location {
  line-height: 55px;
  width: 138px;
  border-right: 1px solid #f2f2f2;
  font-size: 14px;
}

.header__guests {
  line-height: 55px;
  width: 106px;
  border-right: 1px solid #f2f2f2;
  font-size: 14px;
  color: #bdbdbd;
}

.header__searchButton {
  width: 53px;
}

.header__searchIcon {
  line-height: 55px;
  font-size: 20px;
  color: #eb5757;
}

fieldset {
  height: 55px;
  padding: 0;
  border: none;
  margin: 0;
}

legend {
  position: absolute;
  top: 12px;
  left: 28px;
  font-weight: 800;
  font-size: 9px;
  line-height: 11px;
}

input:focus {
  outline: 1px #333333 solid;
}
</style>
