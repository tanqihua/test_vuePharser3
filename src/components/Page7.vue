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
          <h2 :style="`text-align : center`">Your spirit shoe?</h2>
          <ul class="section7_shoeContaienr">
            <li @click="quationsData.quation6 = 'A'">
              <div
                class="imgContainer"
                :style="`height : ${innerHeight * 0.13}px;`"
              >
                <div
                  class="circle"
                  :class="
                    quationsData.quation6 === 'A' ? '--active_sellected' : ''
                  "
                  :style="`
                  height : ${innerHeight * 0.09}px; 
                  width : ${innerHeight * 0.09}px`"
                />
                <img src="/shoes/01shoes.png" alt="01shoes" />
              </div>
            </li>
            <li @click="quationsData.quation6 = 'B'">
              <div
                class="imgContainer"
                :style="`height : ${innerHeight * 0.13}px;`"
              >
                <div
                  class="circle"
                  :class="
                    quationsData.quation6 === 'B' ? '--active_sellected' : ''
                  "
                  :style="`
                  height : ${innerHeight * 0.09}px; 
                  width : ${innerHeight * 0.09}px`"
                />
                <img src="/shoes/02shoes.png" alt="02shoes" />
              </div>
            </li>
            <li @click="quationsData.quation6 = 'C'">
              <div
                class="imgContainer"
                :style="`height : ${innerHeight * 0.13}px;`"
              >
                <div
                  class="circle"
                  :class="
                    quationsData.quation6 === 'C' ? '--active_sellected' : ''
                  "
                  :style="`
                  height : ${innerHeight * 0.09}px; 
                  width : ${innerHeight * 0.09}px`"
                />
                <img src="/shoes/03shoes.png" alt="03shoes" />
              </div>
            </li>
            <li @click="quationsData.quation6 = 'D'">
              <div
                class="imgContainer"
                :style="`height : ${innerHeight * 0.13}px;`"
              >
                <div
                  class="circle"
                  :class="
                    quationsData.quation6 === 'D' ? '--active_sellected' : ''
                  "
                  :style="`
                  height : ${innerHeight * 0.09}px; 
                  width : ${innerHeight * 0.09}px`"
                />
                <img src="/shoes/04shoes.png" alt="04shoes" />
              </div>
            </li>
            <li @click="quationsData.quation6 = 'E'">
              <div
                class="imgContainer"
                :style="`height : ${innerHeight * 0.13}px;`"
              >
                <div
                  class="circle"
                  :class="
                    quationsData.quation6 === 'E' ? '--active_sellected' : ''
                  "
                  :style="`
                  height : ${innerHeight * 0.09}px; 
                  width : ${innerHeight * 0.09}px`"
                />
                <img src="/shoes/05shoes.png" alt="05shoes" />
              </div>
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
  background-color: #e87d8c !important;
}

.--extra_padding {
  padding: 5% 0;
}
.--color_white {
  color: #fff;
}
.section7_shoeContaienr {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
}
.section7_shoeContaienr img {
  height: 100%;
}
.section7_shoeContaienr li {
  padding: 0 !important;
}
.section7_shoeContaienr li .imgContainer {
  position: static;
  transform: translate(0, 0);
}
.circle {
  border-radius: 50%;
  position: absolute;
  background-color: #ffc9d3;
  z-index: -1;
  left: 50%;
  transform: translateX(-50%);
  bottom: 5%;
}
</style>
