<template>
  <header>
    <h1>
      <img
        alt="Vue logo"
        src="../images/logo.svg"
      >
    </h1>
    <div class="header__search">
      <span class="header__location">Helsinki, Finland</span>
      <span class="header__guests">Add guests</span>
      <div class="header__searchButton">
        <span class="material-icons header__searchIcon">search</span>
      </div>
    </div>
  </header>
</template>

<style>
header {
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
</style>
