<template>
  <Mug>
    <Cold v-if="isIced" />
    <Hot v-else />
    <Contents>
      <template v-slot:top>
        <Creamer :id="currentCream.id" :name="currentCream.name" :color="currentCream.color"/>
      </template>
      <template v-if="noSyrup" v-slot:mid>
        <Syrup :id="currentSyrup.id" :name="currentSyrup.name" :color="currentBase.color"/>
      </template>
      <template v-else v-slot:mid>
        <Syrup :id="currentSyrup.id" :name="currentSyrup.name" :color="currentSyrup.color"/>
      </template>
      <template v-slot:bottom>
        <Base :id="currentBase.id" :name="currentBase.name" :color="currentBase.color"/>
      </template>
    </Contents>
  </Mug>
</template>
<script setup lang="ts">
import Contents from "./Contents.vue";
import Mug from "./Mug.vue";
import Syrup from "./Syrup.vue";
import Base from "./Base.vue";
import Creamer from "./Creamer.vue";
import Hot from "./Hot.vue";
import Cold from "./Cold.vue";
import { BaseBeverageType, CreamerType, SyrupType} from "../stores/beverage";

type Props = {
  isIced: boolean;
  noSyrup: boolean;
  currentBase: BaseBeverageType;
  currentCream: CreamerType;
  currentSyrup: SyrupType;
};
defineProps<Props>();
</script>