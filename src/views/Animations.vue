<template>
  <div itemscope itemtype="schema.org/MusicGroup">
    <h1 itemprop="name">Guns n' Roses</h1>
    <ul id="list" class="list">
      <li
        v-for="(member, index) in members"
        v-bind:key="index"
        class="list__item"
        itemscope
        itemtype="schema.org/Person"
      >
        <span class="list__item-num">0{{ index + 1 }}</span>
        <h2 class="list__item-name" itemprop="name">{{ member.name }}</h2>
        <p class="list__item-post" itemprop="jobTitle">
          /&nbsp;{{ member.post }}
        </p>
        <div class="flip-card">
          <div class="flip-card__inner">
            <div
              class="flip-card__front"
              itemscope
              itemtype="https://schema.org/ImageObject"
            >
              <img
                :src="getImgUrl(`members/${member.img}-black-white.jpg`)"
                class="flip-card__photo"
                v-bind:alt="member.name"
                itemprop="contentUrl"
              />
            </div>
            <div
              class="flip-card__back"
              itemscope
              itemtype="https://schema.org/ImageObject"
            >
              <img
                :src="getImgUrl(`members/${member.img}.jpg`)"
                class="flip-card__photo"
                v-bind:alt="member.name"
                itemprop="contentUrl"
              />
            </div>
          </div>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "Animations",
  data: () => {
    return {
      members: [
        {
          name: "Axl Rose",
          post: "lead vocal, piano",
          img: "axl"
        },
        {
          name: "Duff McKagan",
          post: "bass guitar",
          img: "duff"
        },
        {
          name: "Slash",
          post: "lead and rhythm guitars",
          img: "slash"
        },
        {
          name: "Izzy Stradlin",
          post: "rhythm and lead guitars",
          img: "izzy"
        },
        {
          name: "Steven Adler",
          post: "drums and percussion",
          img: "steven"
        }
      ],
      getImgUrl(img) {
        return require("../assets/" + img);
      }
    };
  }
};
</script>

<style scoped lang="scss">
@import "../styles/base/vars.scss";
@import "../styles/utils/mixins.scss";

.flip-card {
  @include absolute($top: 0, $right: 0, $bottom: 0);

  margin: auto;
  transform: translateX(100%);
  opacity: 0;
  transition: $transition-duration-base opacity,
    $transition-duration-base transform;
}

.list {
  max-width: 550px;
  margin: 60px auto 0;

  &__item {
    position: relative;

    @include flex($align: center);

    padding: 15px 150px 15px 0;
    cursor: pointer;

    &-num {
      margin-right: 30px;

      @include typography($weight: 700, $size: 14px);

      opacity: 0;
      transition: $transition-duration-base opacity;
      cursor: pointer;
    }

    &-name {
      transition: $transition-duration-base color;
    }

    &-post {
      opacity: 0;
      transition: $transition-duration-base opacity,
        $transition-duration-base padding-left;
    }

    &:hover {
      .list__item-num {
        opacity: 1;
      }

      .list__item-name {
        color: darken(#fd2e2e, 0.5);
      }

      .list__item-post {
        padding-left: 10px;
        opacity: 1;
      }

      .flip-card {
        opacity: 1;
        transform: translateX(0);
      }
    }
  }
}
</style>
