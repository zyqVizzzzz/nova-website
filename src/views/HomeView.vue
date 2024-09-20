<template>
	<main class="main" v-if="!isMobile">
		<HomePCView />
	</main>
	<main class="main-mobile" v-else>
		<HomeMobileView />
	</main>
	<!-- <div v-else></div> -->
</template>

<script setup>
import { ref, reactive, onMounted, onUnmounted } from "vue";
import HomeMobileView from "./HomeMobileView.vue";
import HomePCView from "./HomePCView.vue";

const isMobile = ref(false);

onMounted(() => {
	checkWindowWidth();
	// 监听窗口大小变化
	window.addEventListener("resize", checkWindowWidth);
});

const checkWindowWidth = () => {
	// 根据窗口宽度判断是否是移动端
	if (isMobileDevice() || window.innerWidth < 768) {
		isMobile.value = true;
	} else {
		isMobile.value = false;
	}
};

const isMobileDevice = () => {
	return (
		/Mobi|Android|iPhone/i.test(navigator.userAgent) ||
		("ontouchstart" in window && screen.width < 768)
	);
};
</script>

<style scoped>
.main {
	max-width: 1440px;
	min-width: 1280px;
}
.main-mobile {
	width: 100vw;
	max-width: 100vw;
}
</style>
