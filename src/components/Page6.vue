<template>
  <div class="page5">
    <!-- <div class="block" :style="`height : ${innerHeight * 0.5}px`" /> -->
    <transition appear @before-enter="beforeEnter" @enter="enter">
      <div>
        <div
          class="container"
          :style="`height : ${innerHeight * 0.55}px; width : ${
            (innerHeight * 0.55 * 736) / 1103
          }px;`"
        >
          <h2 :style="`text-align : center`">
            Who or what helps <br />you to overcome <br />obstacles?
          </h2>
          <ul>
            <li
              :class="quationsData.quation5 === 'A' ? '--active_sellected' : ''"
              @click="quationsData.quation5 = 'A'"
              class="--extra_padding"
            >
              <h6 :class="quationsData.quation5 === 'A' ? '--color_white' : ''">
                Remembering I'm that b*tch
              </h6>
            </li>
            <li
              :class="quationsData.quation5 === 'B' ? '--active_sellected' : ''"
              @click="quationsData.quation5 = 'B'"
              class="--extra_padding"
            >
              <h6 :class="quationsData.quation5 === 'B' ? '--color_white' : ''">
                Netflix and chill ;)
              </h6>
            </li>
            <li
              :class="quationsData.quation5 === 'C' ? '--active_sellected' : ''"
              @click="quationsData.quation5 = 'C'"
              class="--extra_padding"
            >
              <h6 :class="quationsData.quation5 === 'C' ? '--color_white' : ''">
                (Retail) therapy
              </h6>
            </li>
            <li
              :class="quationsData.quation5 === 'D' ? '--active_sellected' : ''"
              @click="quationsData.quation5 = 'D'"
              class="--extra_padding"
            >
              <h6 :class="quationsData.quation5 === 'D' ? '--color_white' : ''">
                My homies Ben & Jerry
              </h6>
            </li>
            <li
              :class="quationsData.quation5 === 'E' ? '--active_sellected' : ''"
              @click="quationsData.quation5 = 'E'"
              class="--extra_padding"
            >
              <h6 :class="quationsData.quation5 === 'E' ? '--color_white' : ''">
                The weekend
              </h6>
            </li>
          </ul>
        </div>
        <div class="block" :style="`height : ${innerHeight * 0.05}px`" />
        <div class="btn-next">
          <button @click="next">back</button>
        </div>
      </div>
    </transition>
  </div>
</template>

<script>
import gsap from "gsap";
export default {
  props: {
    next: {
      type: Function,
      required: true,
    },
    back: {
      type: Function,
      required: true,
    },
    innerHeight: {
      type: Number,
      required: true,
    },
    innerWidth: {
      type: Number,
      required: true,
    },
    quationsData: {
      type: Object,
      required: true,
    },

    current: {
      type: Number,
      required: true,
    },
    nextPage: {
      type: Function,
      required: true,
    },
    setCurrent: {
      type: Function,
      required: true,
    },
    setAction: {
      type: Function,
      required: true,
    },
    action: {
      type: String,
      required: true,
    },
  },
  data() {
    return {
      sellected_item: null,
    };
  },

  methods: {
    beforeEnter(el) {
      el.style.opacity = "0";
    },
    // where the animation will end up
    enter(el) {
      gsap.to(el, {
        duration: 1,
        y: 0,
        opacity: 1,
        delay: 0.8,
        type: "ease",
      });
    },
    next() {
      window.flipCard_empty_reverse();
      this.$emit("setAction", "back");
      this.$emit("back");
    },
  },

  watch: {
    quationsData: {
      handler: function (val) {
        if (val.quation3 !== null) {
          this.sellected_item = val.quation3;
        }
      },
      deep: true,
    },
    sellected_item: {
      handler: function (val) {
        if (val !== null) {
          setTimeout(() => {
            this.$emit("setAction", "next");
            this.$emit("next");
          }, 700);
        }
      },
      deep: true,
    },
  },
};
</script>

<style>
.--active_sellected {
  background-color: #e87d8c;
}

.--extra_padding {
  padding: 5% 0;
}
.--color_white {
  color: #fff;
}
</style>
