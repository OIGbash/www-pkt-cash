<template>
  <footer class="c-footer">
    <div class="container">
      <div class="c-footer__wrap">
        <div class="c-footer__logo">
          <figure class="c-footer__logo-img">
            <img src="/img/logo-white.svg" alt />
          </figure>
        </div>
        <div class="c-footer__menu">
          <h5 class="c-footer__menu-title">{{ $t("footer.quicklink") }}</h5>
          <ul class="c-footer__menu-list">
            <li class="c-footer__menu-item">
              <a href="https://docs.pkt.cash/en/latest/mining/" class="c-footer__menu-link">
                <span class="c-footer__menu-text">{{ $t("footer.setup_pktcrypt") }}</span>
              </a>
            </li>
            <li v-for="(item, index) of quick_links" :key="index" class="c-footer__menu-item">
              <nuxt-link :to="item.route_link" class="c-footer__menu-link">
                <span class="c-footer__menu-text">{{ item.name }}</span>
              </nuxt-link>
            </li>
            <li class="c-footer__menu-item">
              <a href="https://crypto.pkt.cash/" class="c-footer__menu-link">
                <span class="c-footer__menu-text">{{ $t("header.blog") }}</span>
              </a>
            </li>
          </ul>
        </div>
        <div class="c-footer__menu">
          <h5 class="c-footer__menu-title">{{ $t("footer.about") }}</h5>
          <ul class="c-footer__menu-list">
            <li v-for="(item, index) of about_links" :key="index" class="c-footer__menu-item">
              <template v-if="item.name === 'About'">
                <a
                  :href="item.route_link"
                  :class="{ 'link-active' : $route.name === 'about'}"
                  class="c-footer__menu-link"
                >
                  <span class="c-footer__menu-text">{{ item.name }}</span>
                </a>
              </template>
              <template v-else>
                <nuxt-link :to="item.route_link" class="c-footer__menu-link">
                  <span class="c-footer__menu-text">{{ item.name }}</span>
                </nuxt-link>
              </template>
            </li>
          </ul>
        </div>
        <div class="c-footer__menu">
          <h5 class="c-footer__menu-title">Github</h5>
          <ul class="c-footer__menu-list">
            <li v-for="(item, index) of github_links" :key="index" class="c-footer__menu-item">
              <a :href="item.route_link" target="_blank" class="c-footer__menu-link">
                <span class="c-footer__menu-text">{{ item.name }}</span>
              </a>
            </li>
          </ul>
        </div>
        <div class="c-footer__menu">
          <h5 class="c-footer__menu-title">{{ $t("footer.join_community") }}</h5>
          <ul class="c-footer__menu-list">
            <li v-for="(item, index) of join_community" :key="index" class="c-footer__menu-item">
              <a :href="item.route_link" target="_blank" class="c-footer__menu-link">
                <!--<span class="c-footer__menu-text c-footer__menu-text-with-social">
                  <figure class="c-footer__menu-img">
                    <img :src="item.icon" alt />
                  </figure>-->
                  <span class="c-footer__menu-text">{{ item.name }}</span>
                <!--</span>-->
              </a>
            </li>
          </ul>
        </div>
        <div class="c-footer__text">
          <span class="c-footer__text-light">
            <a href="https://github.com/cjdelisle/CJDNS-contact" target="_blank" class="c-footer__menu-link">
              ©2021 PKT Cash | {{ $t("footer.policy") }}
            </a>
          </span>
        </div>
      </div>
    </div>
  </footer>
</template>

<script>
export default {
  name: "Footer",
  data() {
    return {
      // PKT
      // About
      // Roadmap
      // Origin Story
      // Community
      nav_open: false,
      quick_links: [
        {
          name: this.$t("header.mining"),
          route_link: "/mining",
        },
        {
          name: this.$t("header.network_st"),
          route_link: "/network-steward",
        },
        {
          name: this.$t("footer.network_steward_voting"),
          route_link: "/network-steward-vote",
        },
        {
          name: this.$t("header.wallet"),
          route_link: "/wallet",
        }
      ],
      about_links: [
        {
          name: "PKT",
          route_link: "/cash",
        },
        {
          name: this.$t("footer.about"),
          route_link: "/about",
        },
        {
          name: this.$t("header.roadmap"),
          route_link: "/roadmap",
        },
        {
          name: this.$t("footer.origin_story"),
          route_link: "/origin-story",
        },
        {
          name: this.$t("header.community"),
          route_link: "/community",
        },
		    {
          name: this.$t("footer.trademark"),
          route_link: "/trademark",
        },
		    {
          name: this.$t("footer.brand"),
          route_link: "/brand",
        },
      ],
      github_links: [
        {
          name: "pkt.cash",
          route_link: "https://github.com/pkt-cash/",
        },
        {
          name: "cjdns",
          route_link: "https://github.com/cjdelisle/cjdns",
        },
        {
          name: "PacketCrypt",
          route_link: "https://github.com/cjdelisle/PacketCrypt",
        },
      ],
      join_community: [
        {
          name: this.$t("footer.pkt_chat"),
          route_link: "https://pkt.chat",
          //icon: "/img/icon/telegram.svg",
        },
        {
          name: this.$t("footer.twitter"),
          route_link: "https://twitter.com/pkt_cash",
          //icon: "/img/icon/matrix.svg",
        },
        {
          name: this.$t("footer.matrix"),
          route_link: "https://matrix.to/#/#pkt:matrix.org",
          //icon: "/img/icon/matrix.svg",
        },
        /*{
          name: "Instagram",
          route_link: "https://www.instagram.com/pktcash/",
          icon: "/img/icon/instagram.svg",
        },
        {
          name: "Facebook",
          route_link: "https://www.facebook.com/PKT-110041354126488",
          icon: "/img/icon/facebook.svg",
        },*/
      ],
    };
  },
};
</script>

<style lang="scss">
.c-footer {
  background-color: $black;
  color: $white;

  & .container {
    width: 100%;
    max-width: rem(1300);
    padding: rem(76) rem(60);
    @include for-width(-tablet) {
      padding: rem(30) rem(25);
    }
    margin: 0 auto;
  }

  &__wrap {
    display: flex;
    flex-wrap: wrap;
    position: relative;
  }

  &__logo {
    margin-right: rem(104);
    @include for-width(-tablet-lg) {
      margin-right: rem(35);
      margin-bottom: rem(35);
    }
    @include for-width(-tablet) {
      width: 60%;
      margin-right: 0;
      order: 4;

      & img {
        height: rem(25);
      }
    }
  }

  &__menu {
    margin-right: rem(85);

    @include for-width(-desktop-med) {
      margin-right: rem(55);
      margin-bottom: rem(35);
    }
    @include for-width(-tablet-lg) {
      margin-right: rem(32);
      margin-bottom: rem(35);
    }
    @include for-width(-tablet) {
      width: 50%;
      margin-right: 0;
      margin-bottom: 0;
    }

    @include for-width(-tablet) {
      &:nth-child(2) {
        /*order: 1;*/
      }

      &:nth-child(3) {
        /*width: 100%;*/
        /*order: 3;*/
      }

      &:nth-child(5) {
        /*order: 2;*/
        position: static;
        margin-bottom: rem(45);

        &::after {
          content: "";
          left: 0;
          position: absolute;
          width: 100%;
          height: rem(1);
          background-color: $white;
          opacity: 0.1;
          margin-top: rem(14);
        }
      }
    }

    &-title {
      font-family: arial, sans-serif;
      font-weight: 700;
      letter-spacing: 1.1px;
      @include font_sizes(15, 20);
      margin-bottom: rem(23);
      @include for-width(-tablet) {
        @include font_sizes(11, 19);
        margin-bottom: rem(8);
      }
      @include for-width(-tablet) {
        opacity: 0.5;
      }
    }

    &-item {
      margin-bottom: rem(20);
      @include for-width(-tablet) {
        margin-bottom: rem(8);
      }

      &:last-child {
        margin-bottom: rem(4);
        @include for-width(-tablet) {
          margin-bottom: rem(12);
        }
      }
    }

    &-link {
      font-family: arial, sans-serif;
      letter-spacing: 0.85px;
      @include font_sizes(15, 20);
      @include for-width(-small-lg) {
        @include font_sizes(11, 16);
      }
      color: $white;
    }

    &-text {
      position: relative;

      display: flex;
      align-items: center;

      &-with-social {
        padding-left: rem(37);
        @include for-width(-tablet) {
          padding-left: rem(28);
        }
      }
    }

    &-img {
      position: absolute;
      top: 50%;
      left: rem(8);
      transform: translate(-33%, -50%);

      display: flex;
      align-items: center;

      @include for-width(-tablet) {
        transform: translate(-33%, -50%) scale(0.65);
      }

      // max-width: rem(25);
      // height: rem(25);
    }
  }

  &__text {
    width: 100%;
	text-align: center;
	padding-top: rem(25);
    @include for-width(-tablet) {
      width: 40%;
      order: 5;
      padding-top: 0;
	  text-align: left;
    }

    &-light {
      opacity: 0.4;
      font-family: arial, sans-serif;
      letter-spacing: 1.1px;
      @include font_sizes(15, 20);
      @include for-width(-tablet) {
        @include font_sizes(11, 19);
      }
    }
  }
}
</style>
