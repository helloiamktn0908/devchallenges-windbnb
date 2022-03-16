<script lang="ts">
import { defineComponent } from 'vue';

interface Location {
  id: number;
  name: string;
}

export default defineComponent({
  data() {
    return {
      locations: [
        { id: 0, name: 'Helsinki, Finland' },
        { id: 1, name: 'Turku, Finland' },
        { id: 2, name: 'Oulu, Finland' },
        { id: 3, name: 'Vasa, Finland' },
      ] as Location[],
      selectedLocationId: 0,
      isClicked: {
        location: false,
        guests: false,
      },
      adultsCount: 0,
      childrenCount: 0,
    };
  },
  computed: {
    selectedLocation(): string {
      const target = this.locations.filter(
        (location) => location.id === this.selectedLocationId
      )[0];
      return target.name;
    },
    totalGuests(): string {
      return `${this.adultsCount + this.childrenCount} guests`
    }
  },
  methods: {
    select(id: number) {
      console.log(id);
      this.selectedLocationId = id;
      this.isClicked.location = false;
    },
    clickLocation() {
      this.isClicked.guests = false;
      this.isClicked.location = true;
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
  },
});
</script>

<template>
  <div class="drawer">
    <div class="drawer__search">
      <div class="drawer__location_wrapper">
        <fieldset>
          <legend>LOCATION</legend>
          <input
            type="text"
            label="location"
            class="drawer__location"
            :value="selectedLocation"
            @click="clickLocation"
          >
        </fieldset>
        <ul
          v-if="isClicked.location"
          class="drawer__location_ul"
        >
          <li
            v-for="location in locations"
            :key="location.id"
            class="drawer__location_list"
            @click="select(location.id)"
          >
            <span class="material-icons drawer__locationOn_icon">location_on</span>
            {{ location.name }}
          </li>
        </ul>
      </div>
      <div class="drawer__guests_wrapper">
        <fieldset>
          <legend>GUESTS</legend>
          <input
            type="text"
            class="drawer__guests"
            placeholder="Add guests"
            :value="totalGuests"
            @click="clickGuests"
          >
        </fieldset>
        <div
          v-if="isClicked.guests"
          class="drawer__guests_counter"
        >
          <p class="drawer__adultsCounter_title">
            Adults
          </p>
          <p class="drawer__adultsCounter_explanation">
            Ages 13 or above
          </p>
          <button
            class="countButton"
            @click="adultsCountDown"
          >
            -
          </button>
          <span class="counter">{{ adultsCount }}</span>
          <button
            class="countButton"
            @click="adultsCountUp"
          >
            +
          </button>
          <p class="drawer__childrenCounter_title">
            Children
          </p>
          <p class="drawer__childrenCounter_explanation">
            Ages 2-12
          </p>
          <button
            class="countButton"
            @click="childrenCountDown"
          >
            -
          </button>
          <span class="counter">{{ childrenCount }}</span>
          <button
            class="countButton"
            @click="childrenCountUp"
          >
            +
          </button>
        </div>
      </div>
      <div class="drawer__searchButton_wrapper">
        <button class="drawer__searchButton">
          <span class="material-icons drawer__searchIcon">search</span>
          <span>Search</span>
        </button>
      </div>
    </div>

    <div />
  </div>
  <div class="drawer__backGround" />
</template>

<style>
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

.drawer {
  min-height: 460px;
  padding: 2rem 6rem;
}

.drawer__search {
  margin: 42px 0;
  height: 55px;
  border-radius: 16px;
  width: 100%;
  box-shadow: 0px 1px 6px rgba(0, 0, 0, 0.1);
  display: flex;
  justify-content: space-between;
}

.drawer__location_wrapper,
.drawer__guests_wrapper,
.drawer__searchButton_wrapper {
  position: relative;
  width: 100%;
  height: 100%;
}

.drawer__location_wrapper,
.drawer__guests_wrapper {
  border-right: 1px solid #f2f2f2;
  text-align: left;
}

.drawer__searchButton_wrapper {
  display: flex;
  align-items: center;
  justify-content: center;
}

.drawer__location {
  width: calc(100% - 27px * 2 - 2px);
  border-radius: 16px;
  height: calc(100% - 11px - 12px - 2px);
  padding: 21px 27px 3px;
  border: none;
  font-size: 14px;
}

.drawer__guests {
  width: calc(100% - 27px * 2 - 2px);
  border-radius: 16px;
  height: calc(100% - 11px - 12px - 2px);
  padding: 21px 27px 3px;
  border: none;
  font-size: 14px;
}

.drawer__guests::placeholder {
  color: #bdbdbd;
}

.drawer__guests_counter {
  padding-left: 27px;
}

.drawer__adultsCounter_title,
.drawer__childrenCounter_title {
  margin-top: 34px;
  margin-bottom: 0;
  font-size: 14px;
  font-weight: 700;
}

.drawer__adultsCounter_explanation,
.drawer__childrenCounter_explanation {
  font-size: 14px;
  color: #bdbdbd;
  margin: 2px 0 12px;
}

.counter {
  font-size: 14px;
  font-weight: 700;
  margin: 0 8px;
}

.countButton {
  background-color: white;
  border-radius: 5px;
  border: 1px #828282 solid;
  color: #828282;
}

.drawer__searchButton {
  width: 127px;
  height: 48px;
  border-radius: 16px;
  border: none;
  background-color: #eb5757;
  color: white;
  font-weight: 700;
  display: flex;
  align-items: center;
  justify-content: center;
}

.drawer__searchButton:hover {
  cursor: pointer;
  background-color: #eb7676;
}

.drawer__searchIcon {
  font-size: 20px;
  margin-right: 5px;
}

.drawer__location_ul {
  list-style: none;
  padding-left: 27px;
}

.drawer__location_list {
  display: flex;
  font-size: 14px;
  margin-top: 34px;
}

.drawer__location_list:hover {
  cursor: pointer;
}

.drawer__locationOn_icon {
  color: #4f4f4f;
  font-size: 20px;
  margin-right: 10px;
}

.drawer__backGround {
  position: relative;
  background-color: rgba(79, 79, 79, 0.4);
  width: 100vw;
  height: 100vh;
  z-index: 1;
}
</style>
