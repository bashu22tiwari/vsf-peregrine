<template>
  <div class="banner-grid sf-banner-grid">
    <div class="sf-banner-grid__row">
      <div class="sf-banner-grid__col">
        <a v-if="banners[0].link" @click="link(banners[0])">
          <SfBanner
            :subtitle="banners[0].subtitle"
            :title="banners[0].title"
            :description="banners[0].text"
            :button-text="banners[0].buttontext"
            :image="image(banners[0].imageLinkType, banners[0].image)"
            :style="{ '--banner-title-color':  banners[0].textColor, '--banner-description-color':  banners[0].textColor, '--banner-subtitle-color':  banners[0].textColor}"
          />
        </a>
        <SfBanner
          v-else
          :subtitle="banners[0].subtitle"
          :title="banners[0].title"
          :description="banners[0].text"
          :image="image(banners[0].imageLinkType, banners[0].image)"
          :style="{ '--banner-title-color':  banners[0].textColor, '--banner-description-color':  banners[0].textColor, '--banner-subtitle-color':  banners[0].textColor}"
        />
      </div>
    </div>
    <div class="sf-banner-grid__row">
      <div class="sf-banner-grid__col">
        <a v-if="banners[1].link" @click="link(banners[1])">
          <SfBanner
            :subtitle="banners[1].subtitle"
            :title="banners[1].title"
            :description="banners[1].text"
            :button-text="banners[1].buttontext"
            :image="image(banners[1].imageLinkType, banners[1].image)"
            :style="{ '--banner-title-color':  banners[1].textColor, '--banner-description-color':  banners[1].textColor, '--banner-subtitle-color':  banners[1].textColor}"
          />
        </a>
        <SfBanner
          v-else
          :subtitle="banners[1].subtitle"
          :title="banners[1].title"
          :description="banners[1].text"
          :image="image(banners[1].imageLinkType, banners[1].image)"
          :style="{ '--banner-title-color':  banners[1].textColor, '--banner-description-color':  banners[1].textColor, '--banner-subtitle-color':  banners[1].textColor}"
        />
      </div>
      <div class="sf-banner-grid__col">
        <a v-if="banners[2].link" @click="link(banners[2])">
          <SfBanner
            :subtitle="banners[2].subtitle"
            :title="banners[2].title"
            :description="banners[2].text"
            :button-text="banners[2].buttontext"
            :image="image(banners[2].imageLinkType, banners[2].image)"
            :style="{ '--banner-title-color':  banners[2].textColor, '--banner-description-color':  banners[2].textColor, '--banner-subtitle-color':  banners[2].textColor}"
          />
        </a>
        <SfBanner
          v-else
          :subtitle="banners[2].subtitle"
          :title="banners[2].title"
          :description="banners[2].text"
          :image="image(banners[2].imageLinkType, banners[2].image)"
          :style="{ '--banner-title-color':  banners[2].textColor, '--banner-description-color':  banners[2].textColor, '--banner-subtitle-color':  banners[2].textColor}"
        />
      </div>
    </div>
  </div>
</template>

<script>
import { SfBanner } from '@storefront-ui/vue';
import LinkMixin from '../../mixins/LinkMixin';
import imageMixin from '../../mixins/imageMixin';

export default {
  components: {
    SfBanner
  },
  props: {
    componentData: {
      required: true,
      type: Object
    },
    componentType: {
      required: true,
      type: String
    }
  },
  computed: {
    banners () {
      return this.componentData.cards;
    }
  },
  mixins: [LinkMixin, imageMixin]
};
</script>

<style lang="scss" scoped>
@import "~@storefront-ui/shared/styles/helpers";
@import "~@storefront-ui/shared/styles/helpers/breakpoints";

.banner-grid {
  margin: var(--spacer-base) 0;
  @include for-desktop {
    margin: var(--spacer-2xl) 0;
  }
}

// TODO: remove the styling once the production related css issue gets resolved
// copied styling of sf-banner-grid and sf-banner from storefront ui
// >>>>>> starts here

.sf-banner {
  box-sizing: border-box;
  display: var(--banner-display, flex);
  justify-content: var(--banner-justify-content, flex-start);
  width: var(--banner-width, 100%);
  min-height: var(--banner-height, 21.4375rem);
  @include background(
    --banner-background,
    var(--_banner-background-color, transparent),
    var(--_banner-background-image)
  );
  --banner-background-position: 60%;
  &__wrapper {
    display: flex;
    flex-direction: column;
    align-items: var(--banner-align-items, flex-start);
    justify-content: var(--banner-wrapper-justify-content, flex-start);
    flex-direction: var(--banner-wrapper-flex-direction, column);
    padding: var(--banner-padding, var(--spacer-xl));
    flex: 0 0 var(--banner-wrapper-width, 100%);
    text-decoration: none;
    &.sf-button,
    &.sf-button:hover,
    &.sf-button:active {
      --button-background: transparent;
      --button-box-shadow-opacity: 0;
    }
  }
  &__subtitle {
    margin: var(--banner-subtitle-margin, 0);
    color: var(
      --banner-color,
      var(--banner-subtitle-color, var(--c-dark-variant))
    );
    @include font(
      --banner-subtitle-font,
      var(--font-weight--normal),
      var(--font-size--base),
      1.4,
      var(--font-family--secondary)
    );
    text-transform: var(--banner-subtitle-text-transform, uppercase);
  }
  &__title {
    margin: var(--banner-title-margin, var(--spacer-2xs) 0 0 0);
    color: var(--banner-color, var(--banner-title-color, var(--c-text)));
    @include font(
      --banner-title-font,
      var(--font-weight--normal),
      var(--h2-font-size),
      1.4,
      var(--font-family--secondary)
    );
    text-transform: var(--banner-title-text-transform, uppercase);
  }
  &__description {
    display: var(--banner-description-display, none);
    margin: var(
      --banner-description-margin,
      var(--spacer-sm) 0 var(--spacer-base) 0
    );
    color: var(--banner-color, var(--banner-description-color, var(--c-text)));
    text-align: var(--banner-description-text-align, left);
    @include font(
      --banner-description-font,
      var(--font-weight--light),
      var(--font-size--base),
      1.6,
      var(--font-family--primary)
    );
  }
  &__call-to-action {
    --button-color: var(--c-light-variant);
    display: var(--banner-display-call-to-action, none);
  }
  @include for-desktop {
    --banner-background-image: var(
      --_banner-background-desktop-image,
      var(--_banner-background-image)
    );
    --banner-wrapper-width: 50%;
    --banner-description-display: block;
    --banner-display-call-to-action: block;
    --banner-title-margin: var(--spacer-sm) 0 0 0;
    --banner-subtitle-color: var(--c-gray);
    align-items: var(--banner-align-items, center);
    min-height: var(--banner-height, 25rem);
    &__wrapper {
      pointer-events: none;
    }
    &__call-to-action {
      --button-padding: var(--spacer-sm) var(--spacer-xl);
      pointer-events: auto;
    }
    &--right {
      --banner-justify-content: flex-end;
    }
  }
}

.sf-banner-grid {
  --banner-align-items: flex-start;
  --banner-container-width: 50%;
  --banner-description-margin: var(--spacer-xl) 0;
  &__row {
    display: var(--banner-grid-row-display, block);
    flex: var(--banner-grid-row-flex);
    margin: var(--banner-grid-row-margin, 0);
    & + & {
      --banner-grid-row-margin: var(--spacer-sm) 0 0 0;
    }
    @media (min-width: $desktop-min) {
      & + & {
        --banner-grid-row-margin: var(--spacer-xl) 0 0 0;
      }
    }
  }
  &__col {
    display: var(--banner-grid-col-display, block);
    flex: var(--banner-grid-col-flex);
    margin: var(--banner-grid-col-margin, 0);
    & + & {
      --banner-grid-col-margin: var(--spacer-sm) 0 0 0;
    }
  }
  @include for-desktop {
    --banner-grid-row-display: flex;
    --banner-grid-row-flex: 0 0 100%;
    --banner-grid-col-display: flex;
    &__row {
      --banner-grid-row-margin: 0;
      & + & {
        --banner-grid-row-margin: var(--spacer-xl) 0 0 0;
      }
    }
    &__col {
      --banner-grid-col-flex: 1;
      flex-wrap: wrap;
      --banner-grid-col-margin: 0;
      & + & {
        --banner-grid-col-margin: 0 0 0 var(--spacer-xl);
      }
      & > .sf-banner,
      & > a {
        display: flex;
        flex: 1;
      }
      &--small {
        --banner-grid-col-flex: 0 1 36%;
      }
      &--medium {
        --banner-grid-col-flex: 0 1 40%;
        --banner-container-width: 70%;
      }
      &--higher {
        --banner-height: 510px;
      }
    }
  }
}

// <<<<<< ends here
</style>
