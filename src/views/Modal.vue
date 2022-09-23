<template>
    <div>
        <div>
            <button class="button" @click =" showModal = true">Show Modal</button>
        </div>
        <transition class="fade" appear>
            <div class="modal-overlay" v-if="showModal" @click =" showModal = true"></div>
        </transition>


    </div>
</template>

<script>
export default {
    name:'Modal'
    data() {

    return {
      showModal: true,
    };
  },
};
</script>

<style scoped>
* {
  margin: 0px;
  padding: 0;
  box-sizing: border-box;
}
body {
  font-family: "montserrat";
}
.button {
  appearance: none;
  outline: none;
  border: none;
  background: none;
  cursor: pointer;

  display: inline-block;
  padding: 15px 25px;
  background-image: linear-gradient(to right, #cc2e5d, #ff5858);
  border-radius: 8px;

  color: #fff;
  font-size: 18px;
  font-weight: 700;
}

.modal-overlay {
  position: absolute;
  top: 0px;
  left: 0px;
  right: 0px;
  bottom: 0px;
  z-index: 98;
  background-color: rgba(0, 0, 0, 0.3);
}
</style>