<script>
import MyBanner from "./MyBanner.vue";
import MyButton from "./components/MyButton.vue";
import MyInput from "./components/MyInput.vue";
import MyDialog from "./components/MyDialog.vue";
export default {
  components: {MyBanner, MyButton, MyInput, qBtn: MyButton, qDialog: MyDialog},
  data() {
    return {
      sayHiList: [
        {
          parentEvent: this.sayHi,
          label: "Mom",
          color: "red",
          textColor: "green",
          size: 0.5,
          round: false,
          square: true,
        },
        {
          parentEvent: this.kissBye,
          label: "Dad",
          color: "lightblue",
          textColor: "purple",
          size: 0.7,
          round: true,
          square: false,
        },
        {
          parentEvent: this.greeting,
          label: "Jack",
          color: "darkgrey",
          textColor: "pink",
          size: 1,
          round: true,
          square: true,
        },
        {
          parentEvent: this.kissBye,
          label: "Mr. Anderson",
          color: "cayan",
          textColor: "blue",
          size: 2,
          round: false,
          square: true,
        },
      ],
      inputValue: null,
      alert: false,
      confirm: false,
    };
  },
  methods: {
    sayHi(n) {
      alert("Hi " + n + "!!");
    },
    kissBye(n) {
      alert("Bye " + n + "!!❤️");
    },
    greeting(n) {
      alert("Greeting " + n + "!!");
    },
    alert123() {
      alert(123);
    },
  },
  watch: {},
  computed: {},
  mounted() {},
};
</script>

<template>
  <div class="body">
    <h1>Quasar Framework copycat</h1>
    <div class="myDialogWrapper">
      <h2>Dialog</h2>
      <q-btn
        label="Alert"
        color="black"
        text-color="white"
        :size="1"
        round
        @parent-event="alert = !alert"
      ></q-btn>
      <q-dialog v-model="alert">
        <div>
          Lorem ipsum dolor sit amet consectetur adipisicing elit. Rerum
          repellendus sit voluptate voluptas eveniet porro. Rerum blanditiis
          perferendis totam, ea at omnis vel numquam exercitationem aut, natus
          minima, porro labore.
        </div>
        <q-btn
          label="CLose"
          color="black"
          text-color="white"
          :size="1"
          round
          @parent-event="alert = !alert"
          float="right"
        ></q-btn>
      </q-dialog>
      <q-btn
        label="Confirm"
        color="black"
        text-color="white"
        :size="1"
        round
        @parent-event="confirm = !confirm"
      ></q-btn>
      <q-dialog v-model="confirm">
        <div>
          Lorem ipsum dolor sit amet consectetur adipisicing elit. Rerum
          repellendus sit voluptate voluptas eveniet porro. Rerum blanditiis
          perferendis totam, ea at omnis vel numquam exercitationem aut, natus
          minima, porro labore.
        </div>
        <q-btn
          label="CLose"
          color="black"
          text-color="white"
          :size="1"
          round
          @parent-event="confirm = !confirm"
          float="right"
        ></q-btn>
      </q-dialog>
    </div>
    <div class="myBannerWrapper">
      <h2>Banner</h2>
      <MyBanner rounded>
        We can't find your saved recipes until you sign in.

        <template v-slot:action>
          <button class="bannerButton">CONTINUE AS A GUEST</button
          ><button class="bannerButton">SIGN IN</button>
        </template>
      </MyBanner>
      <MyBanner rounded>
        If you saw this banner, the banner was being seen by you.

        <template v-slot:action>
          <button class="bannerButton">YES</button
          ><button class="bannerButton">NO</button
          ><button class="bannerButton">😘</button>
        </template>
      </MyBanner>
    </div>
    <div class="myButtonWrapper">
      <h2>Button</h2>
      <MyButton
        v-for="list of sayHiList"
        @parent-event="list.parentEvent"
        :label="list.label"
        :color="list.color"
        :text-color="list.textColor"
        :size="list.size"
        :round="list.round ? true : false"
        :square="list.square ? true : false"
      ></MyButton>
    </div>
    <div class="myInputWrapper">
      <h2>Input</h2>
      <MyInput
        :modelValue="inputValue"
        @update:modelValue="(newValue) => (inputValue = newValue)"
        label="filled"
        filled
      />
      <MyInput
        :modelValue="inputValue"
        @update:modelValue="(newValue) => (inputValue = newValue)"
        label="outlined"
        outlined
      />
    </div>
  </div>
</template>

<style>
* {
  margin: 0;
  padding: 0;
}
.appWrap {
  min-height: 100svh;
  display: grid;
  place-content: center;
  overflow: auto;
}
h2 {
  text-align: center;
  margin: 1rem;
}
.body {
  width: 100%;
  height: 100svh;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 1rem;
  align-content: start;
}

.bannerButton {
  border: none;
  background: inherit;
  color: aliceblue;
  font-size: 0.8rem;
  cursor: pointer;
  padding: 0.5rem;
  position: relative;
}
.bannerButton::after {
  content: "";
  position: absolute;
  inset: 0;
  background-color: white;
  opacity: 0;
  transition: opacity 0.2s linear;
}

.bannerButton:hover::after {
  opacity: 0.2;
}
</style>
