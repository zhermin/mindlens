<script setup lang="ts">
import { ref } from "vue";
import CustomAlert from "./CustomAlert.vue";
import CustomButton from "./CustomButton.vue";

defineProps<{
  msg?: string;
}>();

const counter = ref(0);
</script>

<template>
  <div class="greetings">
    <h1>{{ msg }}</h1>
    <h3>
      By Zac Tam Zher Min [<a href="https://github.com/zhermin" target="_blank"
        >GitHub</a
      >]
    </h3>

    <!-- 4 Alert Themes in 4 Variations -->
    <CustomAlert theme="info">
      <template v-slot:title>A short descriptive header</template>
      <template v-slot:content>
        This is a paragraph of information with additional supporting detail or
        links to help the user understand what they should do.
      </template>
      <template v-slot:alertButtonSecondaryText>Action</template>
      <template v-slot:alertButtonPrimaryText>Action</template>
    </CustomAlert>

    <CustomAlert theme="error">
      <template v-slot:content>A short descriptive content</template>
    </CustomAlert>

    <CustomAlert theme="warning">
      <template v-slot:title>A short descriptive header</template>
      <template v-slot:content>
        This is a paragraph of information with additional supporting detail or
        links to help the user understand what they should do.
      </template>
    </CustomAlert>

    <CustomAlert theme="success">
      <template v-slot:title>A short descriptive header</template>
    </CustomAlert>

    <h3>Counter: {{ counter }}</h3>

    <!-- 4 Buttons in Info Theme in 4 Variations in Primary and Secondary -->
    <div class="buttons">
      <CustomButton theme="info" type="primary" icon="left" @click="counter++"
        >Increment</CustomButton
      >
      <CustomButton theme="info" type="primary" icon="right" @click="counter++"
        >Increment</CustomButton
      >
      <CustomButton theme="info" type="primary" icon="none" @click="counter++"
        >Increment</CustomButton
      >
      <CustomButton
        theme="info"
        type="primary"
        @click="counter++"
      ></CustomButton>
    </div>

    <div class="buttons">
      <CustomButton theme="info" type="secondary" icon="left" @click="counter--"
        >Decrement</CustomButton
      >
      <CustomButton
        theme="info"
        type="secondary"
        icon="right"
        @click="counter--"
        >Decrement</CustomButton
      >
      <CustomButton theme="info" type="secondary" icon="none" @click="counter--"
        >Decrement</CustomButton
      >
      <CustomButton
        theme="info"
        type="secondary"
        @click="counter--"
      ></CustomButton>
    </div>
  </div>
</template>

<style scoped>
h1 {
  font-weight: 500;
  font-size: 2.6rem;
  top: -10px;
}

h3 {
  font-size: 1.2rem;
}

.greetings h1,
.greetings h3 {
  text-align: center;
}

.buttons {
  display: flex;
  place-items: center;
  place-content: center;
  gap: 1rem;
  margin: 1rem 0;
}

@media (min-width: 1024px) {
  .greetings h1,
  .greetings h3 {
    text-align: left;
  }
  .buttons {
    place-content: flex-start;
  }
}
</style>
