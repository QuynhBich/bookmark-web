<template>
  <div class="flex items-end">
    <Icon
      name="fxemoji:anguish"
      class="font-black text-4xl font-mono mr-2 inline-block w-6 h-6"
    />
    <div
      v-if="listQuestion?.length"
      class="flex flex-col space-y-2 text-xs max-w-xs mx-2 items-start"
    >
      <div class="w-full">
        <span
          v-for="(item, i) in listQuestion"
          :key="i"
          class="px-4 py-2 rounded-b-none inline-block bg-gray-300 text-gray-600 w-full"
          :class="[{ 'rounded-t-lg': i === 0 }]"
        >
          <div class="flex items-end">
            <span v-if="i === 0" class="whitespace-pre-wrap w-[95%]">{{
              item
            }}</span>
            <div
              v-else
              class="flex bg-orange-400 text-black p-1 rounded-md items-end justify-center w-full"
            >
              <span class="whitespace-pre-wrap w-[95%]">{{ item }}</span>
              <div
                class="w-5 h-5 rounded-full bg-orange-700 cursor-pointer flex items-end justify-center"
                @click="sendQuestion(item)"
              >
                <Icon
                  name="material-symbols-light:send-rounded"
                  class="w-full h-full pl-1 text-white"
                />
              </div>
            </div>
          </div>
        </span>
      </div>
    </div>
    <div v-else>
      <Icon name="svg-spinners:3-dots-scale" class="w-6 h-6" />
    </div>
  </div>
</template>
<script lang="ts" setup>
const props = defineProps({
  listQuestion: {
    type: Object as PropType<string[]>,
    default: null,
  },
})
const emits = defineEmits(['sendQuestion'])
const sendQuestion = (question: string) => {
  emits('sendQuestion', question)
}
</script>
