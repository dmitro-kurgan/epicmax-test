<template>
  <header class="header" itemscope itemtype="http://schema.org/WPHeader">
    <a href="./" class="logo" itemprop="url" title="State Supply">
      <img src="../assets/logo.svg" alt="State Supply" itemprop="image" />
    </a>
    <div
      class="header__main"
      itemscope
      itemtype="http://schema.org/Organization"
    >
      <div class="header__top">
        <div class="info" itemtype="https://schema.org/Event">
          <a href="tel:8777757705" class="info__tel" itemprop="telephone"
            >(877)755-7705</a
          >
          <span class="info__separate">~</span>
          <span
            class="info__status info__status--success"
            itemprop="eventStatus"
          >
            We're Open!</span
          >
          <span class="info__event">
            Today we close in <span>3 hours&nbsp;</span>at&nbsp;<span
              itemprop="startDate"
              content="2020-09-7T17:00"
              >5 p.m.</span
            >
            time
          </span>
          <a href="#" class="link link--underlined" itemprop="url"
            >Hours of operation</a
          >
        </div>
        <div class="about">
          <span itemprop="foundingDate">EST 1933.</span>
          <a href="#" class="link link--primary" itemprop="url">Our Story</a>
        </div>
      </div>
      <div class="header__middle">
        <form action="" class="form">
          <label for="select">
            <select id="select" class="form-control" name="select">
              <option selected value="1">All departments</option>
              <option value="2">Department 1</option>
              <option value="3">Department 2</option>
            </select>
          </label>
          <label for="search">
            <input
              id="search"
              class="form-control"
              type="search"
              name="search"
              placeholder="SKU, part number, brand or keyword"
            />
          </label>
          <button type="submit" class="btn btn--primary">Search</button>
        </form>
        <nav aria-label="Manage panel">
          <ul class="list">
            <li class="list__item">
              <button class="btn btn--dropdown">Account</button>
            </li>
            <li class="list__item">
              <button class="btn btn--dropdown">Lists</button>
            </li>
            <li class="list__item">
              <button class="btn">Cart</button>
            </li>
          </ul>
        </nav>
      </div>
      <div class="header__bottom">
        <nav aria-label="Site Menu" role="navigation">
          <ul id="menu" class="nav">
            <template v-for="(nav, index) in nav">
              <li
                class="nav__item"
                v-bind:key="index"
                v-bind:class="`nav__item--${nav.mod}`"
              >
                <a href="#" class="nav__link">{{ nav.name }} </a>
              </li>
            </template>
          </ul>
        </nav>
      </div>
    </div>
  </header>
</template>

<script>
export default {
  name: "Home",
  data: () => {
    return {
      nav: [
        {
          name: "Pumps"
        },
        {
          name: "Steam Traps"
        },
        {
          name: "Valves"
        },
        {
          name: "Controls"
        },
        {
          name: "Sensors"
        },
        {
          name: "More",
          mod: "more"
        },
        {
          name: "Brands",
          mod: "brands"
        }
      ]
    };
  }
};
</script>

<style scoped lang="scss">
@import "../styles/base/vars";
@import "../styles/utils/mixins";

.logo {
  @include absolute($top: 0, $left: 20px, $bottom: 0);
  @include size(160px, 148px);

  margin: auto;
}

.info {
  flex-basis: 70%;
  text-align: left;

  &__separate {
    margin: 0 5px;
  }

  &__status {
    &--success {
      color: $success-color;
    }
  }
}

.about {
  margin-left: auto;

  .link {
    margin-left: 5px;
  }
}

.form {
  flex: 1;
  text-align: left;

  input.form-control {
    width: 350px;
    margin-left: -1px;
  }

  .btn {
    margin-left: 10px;
  }
}

.list {
  display: flex;

  &__item {
    border-left: $border;

    .btn {
      height: 60px;
      padding: 0 40px;
    }
  }
}

.nav {
  display: flex;

  &__link {
    display: inline-flex;
    align-items: center;
    height: 50px;
    padding: 0 20px;
    font-size: 14px;
    text-transform: uppercase;
  }

  &__item {
    &:not(.nav__item--more) .nav__link::after {
      @include arrow($dir: "down");

      margin: -6px 0 0 8px;
      content: "";
    }

    &--more {
      .nav__link::after {
        @include size(20px, 16px);

        margin-left: 5px;
        background: url("../assets/icons/three-dots.svg") no-repeat;
        background-size: contain;
        content: "";
      }
    }

    &--brands {
      margin-left: auto;
    }
  }
}

.header {
  position: relative;
  border-top: $border;

  &__top,
  &__middle,
  &__bottom {
    padding-left: 200px;
    border-bottom: $border;
  }

  &__top {
    display: flex;
    padding-top: 10px;
    padding-right: 40px;
    padding-bottom: 10px;
  }

  &__middle {
    display: flex;
    align-items: center;
  }
}
</style>
