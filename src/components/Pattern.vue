<template>
  <div :class="['flex flex-row relative', className]">
    <div
      v-for="(row, rowIdx) in matrix"
      :key="`matrix-row-${rowIdx}`"
      class="flex flex-col relative z-20 border-b"
    >
      <div
        v-for="(column, colIdx) in row"
        :key="`matrix-col-${colIdx}`"
        :class="[
          'bg-transparent border-l border-b border-neutral-600',
          cellClassName,
        ]"
        @click="setClickedCell([rowIdx, colIdx])"
      >
        <div
          v-motion="motionConfig(rowIdx, colIdx)"
          class="bg-[rgba(14,165,233,0.3)] h-12 w-12"
        ></div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue';

const props = defineProps({
  className: String,
  cellClassName: String,
});

const clickedCell = ref(null);

const x = Array(47).fill(0);
const y = Array(30).fill(0);
const matrix = x.map((_, i) => y.map((_, j) => [i, j]));

const setClickedCell = (cell) => {
  clickedCell.value = cell;
};

const getDistance = (rowIdx, colIdx) => {
  if (!clickedCell.value) return 0;
  return Math.sqrt(
    Math.pow(clickedCell.value[0] - rowIdx, 2) +
    Math.pow(clickedCell.value[1] - colIdx, 2)
  );
};

const motionConfig = (rowIdx, colIdx) => {
  const baseConfig = {
    initial: {
      opacity: 0,
    },
    enter: {
      opacity: [0, 1, 0.5],
      transition: {
        duration: 500,
        ease: 'backOut',
      },
    },
    hovered: {
      opacity: [0, 1, 0.5],
      transition: {
        duration: 500,
        ease: 'backOut',
      },
    }
  };

  if (clickedCell.value) {
    const distance = getDistance(rowIdx, colIdx);
    return {
      ...baseConfig,
      clicked: {
        opacity: [0, 1 - distance * 0.1, 0],
        transition: {
          duration: distance * 200,
        },
      }
    };
  }

  return baseConfig;
};
</script>