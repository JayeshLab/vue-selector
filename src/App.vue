<template>
  <div id="app">
    <section>
      <VueSelector :options="option1" multiple v-model="selected" :show="false" layout="horizontal" valueField="id" activeClass="my-selected-item" @change="mychange">
        <template v-slot="{ option }">
          <div class="my-item">
            <span class="chkicon"></span>
            <span class="my-img" v-html="option.icon"></span>
            <span>{{ option.id }}</span>
          </div>
        </template>
      </VueSelector>
      {{ selected }}
    </section>
    <section>
      <VueSelector :options="option1" multiple v-model="selected" :show="true" layout="vertical" valueField="id" activeClass="my-selected-item" @change="mychange">
      </VueSelector>
      {{ selected }}
    </section>
  </div>
</template>

<script>
import VueSelector from "./VueSelector";

export default {
  name: "App",
  data() {
    return {
      selected: [],
      option1: [
        {
          id: "dizzy",
          label: "Dizzy",
          icon: `<svg xmlns="http://www.w3.org/2000/svg" width="100%" height="100%"  fill="currentColor" class="bi bi-emoji-dizzy" viewBox="0 0 16 16">
                  <path d="M8 15A7 7 0 1 1 8 1a7 7 0 0 1 0 14zm0 1A8 8 0 1 0 8 0a8 8 0 0 0 0 16z"/>
                  <path d="M9.146 5.146a.5.5 0 0 1 .708 0l.646.647.646-.647a.5.5 0 0 1 .708.708l-.647.646.647.646a.5.5 0 0 1-.708.708l-.646-.647-.646.647a.5.5 0 1 1-.708-.708l.647-.646-.647-.646a.5.5 0 0 1 0-.708zm-5 0a.5.5 0 0 1 .708 0l.646.647.646-.647a.5.5 0 1 1 .708.708l-.647.646.647.646a.5.5 0 1 1-.708.708L5.5 7.207l-.646.647a.5.5 0 1 1-.708-.708l.647-.646-.647-.646a.5.5 0 0 1 0-.708zM10 11a2 2 0 1 1-4 0 2 2 0 0 1 4 0z"/>
                </svg>`,
        },
        {
          id: "heart-eyes",
          label: "Heart Eyes",
          icon: `<svg xmlns="http://www.w3.org/2000/svg" width="100%" height="100%"  fill="currentColor" class="bi bi-emoji-heart-eyes" viewBox="0 0 16 16">
                  <path d="M8 15A7 7 0 1 1 8 1a7 7 0 0 1 0 14zm0 1A8 8 0 1 0 8 0a8 8 0 0 0 0 16z"/>
                  <path d="M11.315 10.014a.5.5 0 0 1 .548.736A4.498 4.498 0 0 1 7.965 13a4.498 4.498 0 0 1-3.898-2.25.5.5 0 0 1 .548-.736h.005l.017.005.067.015.252.055c.215.046.515.108.857.169.693.124 1.522.242 2.152.242.63 0 1.46-.118 2.152-.242a26.58 26.58 0 0 0 1.109-.224l.067-.015.017-.004.005-.002zM4.756 4.566c.763-1.424 4.02-.12.952 3.434-4.496-1.596-2.35-4.298-.952-3.434zm6.488 0c1.398-.864 3.544 1.838-.952 3.434-3.067-3.554.19-4.858.952-3.434z"/>
                </svg>`,
        },
        {
          id: "smile",
          label: "Smile",
          icon: `<svg xmlns="http://www.w3.org/2000/svg" width="100%" height="100%"   fill="currentColor" class="bi bi-emoji-smile" viewBox="0 0 16 16">
                <path d="M8 15A7 7 0 1 1 8 1a7 7 0 0 1 0 14zm0 1A8 8 0 1 0 8 0a8 8 0 0 0 0 16z"/>
                <path d="M4.285 9.567a.5.5 0 0 1 .683.183A3.498 3.498 0 0 0 8 11.5a3.498 3.498 0 0 0 3.032-1.75.5.5 0 1 1 .866.5A4.498 4.498 0 0 1 8 12.5a4.498 4.498 0 0 1-3.898-2.25.5.5 0 0 1 .183-.683zM7 6.5C7 7.328 6.552 8 6 8s-1-.672-1-1.5S5.448 5 6 5s1 .672 1 1.5zm4 0c0 .828-.448 1.5-1 1.5s-1-.672-1-1.5S9.448 5 10 5s1 .672 1 1.5z"/>
              </svg>`,
        },
        {
          id: "sun glasses",
          label: "Sun Glasses",
          icon: `<svg xmlns="http://www.w3.org/2000/svg" width="100%" height="100%"  fill="currentColor" class="bi bi-emoji-sunglasses" viewBox="0 0 16 16">
                  <path d="M4.968 9.75a.5.5 0 1 0-.866.5A4.498 4.498 0 0 0 8 12.5a4.5 4.5 0 0 0 3.898-2.25.5.5 0 1 0-.866-.5A3.498 3.498 0 0 1 8 11.5a3.498 3.498 0 0 1-3.032-1.75zM7 5.116V5a1 1 0 0 0-1-1H3.28a1 1 0 0 0-.97 1.243l.311 1.242A2 2 0 0 0 4.561 8H5a2 2 0 0 0 1.994-1.839A2.99 2.99 0 0 1 8 6c.393 0 .74.064 1.006.161A2 2 0 0 0 11 8h.438a2 2 0 0 0 1.94-1.515l.311-1.242A1 1 0 0 0 12.72 4H10a1 1 0 0 0-1 1v.116A4.22 4.22 0 0 0 8 5c-.35 0-.69.04-1 .116z"/>
                  <path d="M16 8A8 8 0 1 1 0 8a8 8 0 0 1 16 0zm-1 0A7 7 0 1 0 1 8a7 7 0 0 0 14 0z"/>
                </svg>`,
        },
        {
          id: "angry",
          label: "Angry",
          icon: `<svg xmlns="http://www.w3.org/2000/svg" width="100%" height="100%" fill="currentColor" class="bi bi-emoji-angry" viewBox="0 0 16 16">
                  <path d="M8 15A7 7 0 1 1 8 1a7 7 0 0 1 0 14zm0 1A8 8 0 1 0 8 0a8 8 0 0 0 0 16z"/>
                  <path d="M4.285 12.433a.5.5 0 0 0 .683-.183A3.498 3.498 0 0 1 8 10.5c1.295 0 2.426.703 3.032 1.75a.5.5 0 0 0 .866-.5A4.498 4.498 0 0 0 8 9.5a4.5 4.5 0 0 0-3.898 2.25.5.5 0 0 0 .183.683zm6.991-8.38a.5.5 0 1 1 .448.894l-1.009.504c.176.27.285.64.285 1.049 0 .828-.448 1.5-1 1.5s-1-.672-1-1.5c0-.247.04-.48.11-.686a.502.502 0 0 1 .166-.761l2-1zm-6.552 0a.5.5 0 0 0-.448.894l1.009.504A1.94 1.94 0 0 0 5 6.5C5 7.328 5.448 8 6 8s1-.672 1-1.5c0-.247-.04-.48-.11-.686a.502.502 0 0 0-.166-.761l-2-1z"/>
                </svg>`,
        },
      ],
    };
  },
  methods: {
    mychange(e) {
      console.log("CHANGE ", e);
    },
  },
  components: {
    VueSelector,
  },
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  padding: 50px;
  color: blue;
}

.my-item {
  display: flex;
  position: relative;
  flex-direction: column;
  padding: 20px;
  text-align: center;
  align-items: center;
  justify-content: center;
  width: 100px;
  height: 100px;
  border-radius: 10px;
  border: 1px solid currentColor;
  background: white;
  box-shadow: rgba(0, 0, 0, 0.1) 0px 1px 3px 0px, rgba(0, 0, 0, 0.06) 0px 1px 2px 0px;
  color: lightgrey;
}
.my-item:hover {
  border: 1px solid #b1b1b1;
}
.my-selected-item .my-item {
  border-radius: 10px;
  color: blue;
  border: 1px solid blue;
  box-shadow: rgba(17, 17, 26, 0.1) 0px 4px 16px, rgba(17, 17, 26, 0.05) 0px 8px 32px;
}
.chkicon {
  position: absolute;
  top: -14px;
  left: calc(50% - 13px);
  height: 26px;
  width: 26px;
  border-radius: 100%;
  background: white;
  transform: rotate(50deg);
  transition: background 100ms cubic-bezier(0.165, 0.84, 0.44, 1);
}
.chkicon::before,
.chkicon::after {
  content: "";
  display: block;
  position: absolute;
}
.chkicon::before {
  height: 100%;
  width: 100%;
  border-radius: 100%;
  border: 1px solid lightgrey;
  background: transparent;
  transition: background 100ms cubic-bezier(0.165, 0.84, 0.44, 1);
}

.chkicon::after {
  border: 3px solid transparent;
  transition: height 100ms ease-in, width 100ms ease-out 100ms, border-color cubic-bezier(0.165, 0.84, 0.44, 1) 100ms 100ms;
  width: 0px;
  height: 0px;
  bottom: 4px;
  left: 7px;
  border-radius: 2px;
  transform-origin: bottom left;
}
.my-selected-item .chkicon:after {
  width: 5px;
  height: 12px;
  border-right-color: white;
  border-bottom-color: white;
  transition: width 100ms ease-in, height 100ms ease-out 100ms, border-color cubic-bezier(0.165, 0.84, 0.44, 1) 100ms;
}
.my-selected-item .chkicon:before {
  background: rgb(0, 132, 255);
  border: 1px solid currentColor;
}
.my-img {
  margin-bottom: 10px;
  height: 40px;
  width: 40px;
  color: currentColor;
  text-align: center;
}
</style>
