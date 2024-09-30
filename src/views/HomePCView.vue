<template>
	<nav class="nova-nav">
		<div class="nova-nav_logo"></div>
		<ul class="nova-nav_list">
			<li>Home</li>
			<li @click="linkNavAbout('about')">About nova</li>
			<li @click="linkNavDesc('desc')">Why Choose us</li>
			<li @click="linkNavService('service')">Our services</li>
			<li @click="linkNavPartners('partners')">Partners</li>
		</ul>
		<div class="nova-nav_button">
			<button @click="scrollToSection">Contact Us</button>
		</div>
	</nav>
	<nav class="nova-devide"></nav>
	<div class="nova-hero">
		<div class="nova-hero_banner">
			<div class="nova-hero_banner-logo">N<span>O</span>VA STRATEGY</div>
		</div>
		<div class="nova-hero_title">
			<p>Your Strategic Growth Partner</p>
			<p>And Web3 CMO</p>
		</div>
	</div>
	<div class="nova-about" ref="about">
		<div class="nova-about_title">
			<p>About Nova</p>
		</div>
		<div class="nova-about_detail">
			We're dedicated to amplifying the success of Web3 projects and exchanges
			worldwide. We understand that one size doesn't fit all. Our expert team
			crafts bespoke strategies tailored to the unique characteristics and needs
			of each project. Whether it's boosting user growth, expanding market
			reach, increasing TVL, or maximizing ROl, we're committed to delivering
			results that exceed expectations. Think of us as your in-house CMO, but
			better. With our unparalleled industry expertise and a proven track record
			of success, we've empowered countless exchanges and projects to achieve
			remarkable growth.
		</div>
	</div>
	<div class="nova-desc" ref="desc">
		<div class="nova-about_title">
			<p>Why Choose Us?</p>
		</div>
		<div class="nova-desc_center">
			<div class="nova-desc_center-item">
				<div class="center-item_content">
					<div class="center-item_title">Experts in Growth and Marketing</div>
					Our core team members come from top exchanges and projects. With
					extensive experience in building global markets and driving growth
					from zero to hero, we are well-versed in creating international brand
					strategies and growth plans.
				</div>
			</div>
			<div class="nova-desc_center-item">
				<div class="center-item_content">
					<div class="center-item_title">Extensive & Quality Outreach</div>
					Premium influencer & media resources in various major crypto markets.
					A wide selection of 1800+ global premium influencers, reaching 20M+
					crypto audiences 180B+ Trading Volume Generated
				</div>
			</div>
			<div class="nova-desc_center-item">
				<div class="center-item_content">
					<div class="center-item_title">Industry Know-How</div>
					we advise you on what is the best practices and the most
					cost-efficient way to achieve your goal.
				</div>
			</div>
			<div class="nova-desc_center-item">
				<div class="center-item_content">
					<div class="center-item_title">Top Notch Resources</div>
					industry top partners, global top exchanges, VCs, sport and
					entertainment sponsorship resources etc.
				</div>
			</div>
			<div class="nova-desc_center-logo">N<span>O</span>VA STRATEGY</div>
		</div>
	</div>
	<div class="nova-service" ref="service">
		<div class="nova-service_title">
			<p>Our Services</p>
		</div>
		<ul class="nova-service_list">
			<li
				class="list-item"
				:class="item.active ? 'active' : ''"
				@click="handleServiceToggle(item)"
				@mouseenter="handleServiceToggle(item)"
				v-for="item of serviceList"
			>
				<div class="list-item_logo" :class="`service${item.logo}`"></div>
				<div class="list-item_title">{{ item.title }}</div>

				<div class="list-item_child" v-show="item.active">
					<p v-for="(service, index) in item.childrenList" :key="index">
						{{ service.text }}
					</p>
				</div>
			</li>
		</ul>
	</div>
	<div class="nova-partners" ref="partners">
		<div class="nova-partners_title">
			<p>Partners</p>
		</div>
		<div class="nova-devide"></div>
		<Vue3Marquee
			:duration="20"
			:delay="0"
			direction="left"
			:pauseOnHover="true"
		>
			<div class="nova-partners_group">
				<div class="group-item" v-for="item in partnerList">
					<div
						v-if="item.logo === 'nova'"
						class="group-item_banner"
						:class="`group-item_banner-${item.item}`"
						@click="linkToPage(item.link)"
					></div>
					<div v-else class="group-item_text" @click="linkToPage(item.link)">
						{{ item.text }}
					</div>
				</div>
			</div>
		</Vue3Marquee>
	</div>
	<div class="nova-form" ref="novaform">
		<div class="submit-tip" v-if="isFormTip">
			<p>Submission Successful!</p>
			<p>We will be in touch with you shortly...</p>
		</div>
		<div class="nova-form_title">
			<p>Follow Us</p>
			<p class="twitter-logo" @click="linkToTwitter">
				<img src="../assets/twitter.jpg" alt="" width="52px" />
			</p>
		</div>
		<div class="nova-form_container">
			<div class="nova-form_container-form">
				<div class="form-row">
					<div class="form-group">
						<input type="text" id="first-name" placeholder="First Name" />
					</div>
					<div class="form-group">
						<input type="text" id="last-name" placeholder="Last Name" />
					</div>
				</div>

				<div class="form-row">
					<div class="form-group">
						<input type="text" id="telegram" placeholder="Telegram Username" />
					</div>
					<div class="form-group">
						<input type="email" id="email" placeholder="xxxxx@gmail.com" />
					</div>
				</div>

				<div class="form-row full-width">
					<textarea
						placeholder="Please enter your questions or suggestions for us and we will contact you after receiving the information."
					></textarea>
					<div class="word-count">Number of words: 1000</div>
				</div>

				<div class="form-row button-row">
					<button type="submit" class="submit-button" @click="handleSubmit">
						Contact Us
					</button>
				</div>
			</div>
		</div>
	</div>
	<!-- <div class="nova-devide"></div>
	<footer class="nova-footer">
		<div class="nova-footer_contact">
			<div class="nova-footer_contact-title"></div>
			<div class="nova-footer_contact-detail">
				<div class="contact-detail_item twitter"></div>
				<div class="contact-detail_item youtube"></div>
				<div class="contact-detail_item telegram"></div>
				<div class="contact-detail_item ins"></div>
			</div>
		</div>
		<div class="nova-footer_link">
			<div class="footer-link_item">
				<div class="footer-link_item-title">Company</div>
				<div class="footer-link_item-link">Home</div>
				<div class="footer-link_item-link">About</div>
				<div class="footer-link_item-link">Pricing</div>
				<div class="footer-link_item-link">FAQ</div>
				<div class="footer-link_item-link">Review</div>
				<div class="footer-link_item-link">Contact</div>
			</div>
			<div class="footer-link_item">
				<div class="footer-link_item-title">Product</div>
				<div class="footer-link_item-link">AI Assistant</div>
				<div class="footer-link_item-link">Funnels</div>
				<div class="footer-link_item-link">Exit Intent</div>
				<div class="footer-link_item-link">Popups</div>
				<div class="footer-link_item-link">Automation</div>
				<div class="footer-link_item-link">Personalization</div>
			</div>
			<div class="footer-link_item">
				<div class="footer-link_item-title">Benefits</div>
				<div class="footer-link_item-link">Sales</div>
				<div class="footer-link_item-link">Customers</div>
				<div class="footer-link_item-link">Leads</div>
				<div class="footer-link_item-link">Growth</div>
				<div class="footer-link_item-link">Marketing</div>
				<div class="footer-link_item-link">SEO</div>
				<div class="footer-link_item-link">Search</div>
			</div>
			<div class="footer-link_item">
				<div class="footer-link_item-title">Members</div>
				<div class="footer-link_item-link">Account</div>
				<div class="footer-link_item-link">Community</div>
				<div class="footer-link_item-link">Resources</div>
				<div class="footer-link_item-link">Terms</div>
				<div class="footer-link_item-link">Privacy</div>
			</div>
		</div>
	</footer> -->
	<div class="nova-devide"></div>
	<div class="copyright">
		Copyright 2024 nova strategy · All rights reserved ·
		<span @click="returnToTop">Return to Top</span>
	</div>
</template>
<script setup>
import { ref, reactive, onMounted, onUnmounted } from "vue";
import { Vue3Marquee } from "vue3-marquee";

const novaform = ref(null);
const about = ref(null);
const desc = ref(null);
const service = ref(null);
const partners = ref(null);

const checkWindowWidth = () => {
	// 根据窗口宽度判断是否是移动端
	if (/Mobi|Android|iPhone/i.test(navigator.userAgent)) {
		isMobile.value = true;
	}
};

const isFormTip = ref(false);

const serviceList = reactive([
	{
		logo: "1",
		title: "Global Growth Strategy Consulting",
		active: true,
		childrenList: [
			{ logo: 1, text: "Partnerships and Alliances" },
			{ logo: 2, text: "Marketing and Brand Promotion" },
			{ logo: 3, text: "Security and Compliance" },
			{ logo: 4, text: "Ecosystem Support" },
			{ logo: 5, text: "140+ Media House Globally" },
			{ logo: 6, text: "Governance and Incentive Mechanisms" },
			{
				logo: 7,
				text: "Empowering your global expansion with tailored strategies and comprehensive supportCommunity Building and Management",
			},
		],
	},
	{
		logo: "2",
		active: false,
		title: "Press & Branding",
		childrenList: [
			{ logo: 1, text: "Global media relationship management" },
			{ logo: 2, text: "Local meet up events setup and logistics" },
			{
				logo: 3,
				text: "Over 140 global media outlets in 14+ languages, both crypto, business and tech media, including tier 1, tier 2, and niche media outlets.",
			},
		],
	},
	{
		logo: "3",
		active: false,
		title: "Influencer Marketing",
		childrenList: [
			{ logo: 1, text: "Over 1800+ Influencers" },
			{ logo: 2, text: "Reach 20M+ Audiences" },
			{ logo: 3, text: "100+ Web3 Communities" },
			{
				logo: 4,
				text: "Professional services)",
			},
			{
				logo: 5,
				text: "Cover 34+ Major Countries ( Eglish, Greater China, South Korea, Japan, SEA, South Asia, Korea, LATAM, Turkey, Europe, CIS, more…",
			},
		],
	},
	{
		logo: "4",
		active: false,
		title: "Listing & Fundraising",
		childrenList: [
			{ logo: 1, text: "Reach TOP Exchanges For Token Listing" },
			{ logo: 2, text: "5+ TOP VCs" },
		],
	},
]);

const partnerList = reactive([
	{ item: "1", logo: "nova", link: "https://notco.in/" },
	{ item: "2", logo: "nova", link: "https://www.gaianet.ai/" },
	{ item: "3", logo: "nova", link: "https://www.olab.xyz/" },
	{ item: "4", logo: "nova", link: "https://milady.gg/" },
	{ item: "5", logo: "nova", link: "https://io.net/team" },
	{ item: "6", logo: "nova", link: "https://www.uxlink.io/" },
	{ item: "7", logo: "nova", link: "https://www.kava.io/" },
	{ item: "7", logo: "", text: "Notcoin", link: "https://notco.in/" },
	{ item: "8", logo: "", text: "Gaia", link: "https://www.gaianet.ai/" },
	{ item: "9", logo: "", text: "O.LAB", link: "https://www.olab.xyz/" },
	{ item: "10", logo: "", text: "Milady", link: "https://milady.gg/" },
	{ item: "11", logo: "", text: "io.net", link: "https://io.net/team" },
	{ item: "12", logo: "", text: "UXLINK", link: "https://www.uxlink.io/" },
	{ item: "12", logo: "", text: "Kava", link: "https://www.kava.io/" },
]);

const linkToPage = (link) => {
	window.open(link);
};

const handleSubmit = () => {
	isFormTip.value = true;
	const timer = setTimeout(() => {
		isFormTip.value = false;
		timer = null;
	}, 2000);
};

const handleServiceToggle = (item) => {
	serviceList.forEach((service) => {
		service.active = false;
		if (item.title === service.title) {
			// setTimeout(() => {
			service.active = true;
			// }, 400);
		}
	});
};

const linkToTwitter = () => {
	window.open("https://x.com/thenovastrategy");
};

const scrollToSection = () => {
	novaform.value.scrollIntoView({
		behavior: "smooth", // 平滑滚动
		block: "start", // 滚动到目标元素的顶部
	});
};

const linkNavAbout = () => {
	about.value.scrollIntoView({
		behavior: "smooth", // 平滑滚动
		block: "start", // 滚动到目标元素的顶部
	});
};
const linkNavDesc = () => {
	desc.value.scrollIntoView({
		behavior: "smooth", // 平滑滚动
		block: "start", // 滚动到目标元素的顶部
	});
};
const linkNavService = () => {
	service.value.scrollIntoView({
		behavior: "smooth", // 平滑滚动
		block: "start", // 滚动到目标元素的顶部
	});
};
const linkNavPartners = () => {
	partners.value.scrollIntoView({
		behavior: "smooth", // 平滑滚动
		block: "start", // 滚动到目标元素的顶部
	});
};

/**
 * Returns the user to the top of the page.
 * @return {void}
 */
const returnToTop = () => {
	window.scrollTo({
		top: 0,
		behavior: "smooth", // 平滑滚动
	});
};
</script>

<style scoped>
.submit-tip {
	position: absolute;
	top: 40%;
	left: 50%;
	transform: translateX(-50%);
	width: 300px;
	background: rgba(30, 30, 30, 0.8);
	text-align: left;
	padding: 20px;
	line-height: 20px;
	font-size: 14px;
	border-radius: 10px;
	color: #888;
	transition: all 0.4s ease;
}
.submit-tip > p {
	height: 20px;
}
.nova-nav {
	position: relative;
	height: 75px;
	text-align: center;
	line-height: 75px;
	display: flex;
	align-items: center;
	padding: 0 30px;
	box-sizing: border-box;
	justify-content: space-between;
}
.nova-nav_logo {
	width: 85px;
	height: 30px;
	background-image: url("../assets/banner.jpg");
	background-size: cover;
}
.nova-nav_list {
	color: #d8d8d8;
	display: flex;
	width: 640px;
	justify-content: space-between;
}
.nova-nav_list > li {
	list-style-type: none;
	cursor: pointer;
}
.nova-nav_button > button {
	width: 120px;
	height: 36px;
	/* background: #944efc; */
	border: 1px solid #944efc;
	border-radius: 36px;
	font-size: 15px;
	color: #d8d8d8;
	cursor: pointer;
	background: #020014; /* 背景色是渐变的起始色 */
	box-shadow: 0 0 20px 5px #944efc inset; /* 渐变效果：从外到内 */
	transition: box-shadow 0.3s ease; /* 平滑过渡效果 */
}
.nova-devide {
	width: 100%;
	height: 1px;
	background-image: url("../assets/banner-line.jpg");
	background-repeat: no-repeat;
	background-size: contain;
}
.nova-hero {
	height: 750px;
	background-image: url("../assets/hero-banner.jpg");
	background-repeat: no-repeat;
	background-size: cover;
	background-position: bottom;
	padding-top: 100px;
	text-align: center;
	color: #fff;
}
.nova-hero_banner {
	margin-bottom: 30px;
	display: flex;
	align-items: center;
	justify-content: center;
}
.nova-hero_banner-logo {
	width: 230px;
	height: 37px;
	background-image: url("../assets/hero-banner3.jpg");
	background-repeat: no-repeat;
	background-size: contain;
	background-position: center;
	display: flex;
	align-items: center;
	justify-content: center;
	letter-spacing: 4px;
	padding-left: 23px;
}
.nova-hero_banner-logo > span {
	color: #944efc;
}

.nova-hero_title {
	margin-bottom: 50px;
	font-size: 42px;
	font-weight: 900;
}
.nova-hero_title > p {
	font-weight: 600;
}
.nova-about {
	/* height: 750px; */
	margin-top: -150px;
	text-align: center;
	color: #fff;
}
.nova-about_title {
	margin-bottom: 20px;
	font-size: 42px;
}
.nova-about_title > p {
	font-weight: 400;
}
.nova-about_detail {
	color: #d8d8d8;
	font-size: 14px;
	width: 880px;
	margin: 0 auto;
}
.nova-desc {
	margin-top: 150px;
	width: 100%;
	height: 560px;
	color: #fff;
	text-align: center;
}
.nova-desc_center {
	margin-top: -50px;
	width: 100%;
	height: 460px;
	background-image: url("../assets/choose.jpg");
	background-repeat: no-repeat;
	background-size: contain;
	background-position: center;
	display: flex;
	flex-wrap: wrap;
	align-items: center;
	position: relative;
}
.nova-desc_center-logo {
	position: absolute;
	width: 234px;
	height: 37px;
	background-image: url("../assets/desc-choose.jpg");
	background-repeat: no-repeat;
	background-size: contain;
	background-position: center;
	left: 50%;
	margin-left: -117px;
	display: flex;
	align-items: center;
	justify-content: center;
	letter-spacing: 4px;
}
.nova-desc_center-logo > span {
	color: #944efc;
}
.nova-desc_center-item {
	width: 50%;
	display: flex;
	justify-content: center;
}
.center-item_title {
	color: #fff;
	font-size: 20px;
	margin-bottom: 10px;
}
.center-item_content {
	width: 75%;
	color: #9998a0;
}
.center-item_content > span {
	color: #fff;
}
.nova-service {
	margin-top: 40px;
	margin-bottom: 100px;
	text-align: center;
	color: #fff;
}
.nova-service_title {
	margin-bottom: 20px;
	font-size: 42px;
}
.nova-service_title > p {
	font-weight: 400;
}
.nova-service_list {
	display: flex;
	gap: 10px;
	justify-content: center;
	padding: 0;
	margin: 0;
}

.nova-service_list > li {
	list-style-type: none;
	cursor: pointer;
	width: 150px;
	height: 460px;
	font-size: 18px;
	font-weight: 400;
	background-image: url("../assets/service-container.jpg");
	background-repeat: no-repeat;
	background-size: contain;
	border-radius: 20px;
	display: flex;
	flex-direction: column;
	padding: 40px 20px;
	color: white;
	transition: all 0.4s ease;
	position: relative;
	box-shadow: 0 4px 10px rgba(0, 0, 0, 0.3);
}

.nova-service_list > li[v-cloak] {
	display: none;
}
[v-show] {
	opacity: 1;
}

.nova-service_list > li.active {
	font-size: 32px;
	font-weight: 600;
	width: 650px;
	height: 460px;
	background-image: url("../assets/service-active.jpg");
	background-size: 100%;
	padding: 40px;
	box-sizing: border-box;
}

.list-item_logo img {
	width: 40px;
	height: 40px;
}

.list-item_title {
	text-align: left;
	margin-bottom: 10px;
}

.list-item_child {
	opacity: 0;
	max-height: 0;
	overflow: hidden;
	transition: opacity 0.4s ease, max-height 0.4s ease;
	font-size: 14px;
	color: #ccc;
	line-height: 1.6;
	text-align: left;
}
.list-item.active .list-item_child {
	opacity: 1;
	max-height: 230px; /* 根据内容大小调整此值，或使用auto */
}

.nova-service_list > li.active .list-item_child {
	opacity: 1; /* 在激活时显示子元素内容 */
}

.list-item_child p {
	margin: 5px 0;
}

.nova-partners {
	margin-top: 40px;
	margin-bottom: 120px;
	text-align: center;
	color: #fff;
}
.nova-partners_title {
	margin-bottom: 20px;
	font-size: 42px;
}
.nova-partners_title > p {
	font-weight: 400;
}

.nova-partners_group {
	display: flex;
	width: 1540px;
	flex-wrap: wrap; /* 允许项目换行 */
	justify-content: space-between; /* 为了在每行项目间分配空间 */
	margin: 0 auto;
}

.group-item_banner {
	width: 85px;
	height: 30px;
	background-image: url("../assets/banner.jpg");
	background-repeat: no-repeat;
	background-size: contain;
	cursor: pointer;
}

.group-item_text {
	font-size: 30px;
	cursor: pointer;
}

.group-item_banner-1 {
	width: 179px;
	height: 78px;
	background-image: url("../assets/port-notcoin.jpg");
	background-repeat: no-repeat;
	background-size: contain;
	background-position: center;
}
.group-item_banner-2 {
	width: 179px;
	height: 70px;
	background-image: url("../assets/port-gaia.jpg");
	background-repeat: no-repeat;
	background-size: contain;
	background-position: center;
}
.group-item_banner-3 {
	width: 179px;
	height: 70px;
	background-image: url("../assets/port-olab.jpg");
	background-repeat: no-repeat;
	background-size: contain;
	background-position: center;
}
.group-item_banner-4 {
	width: 179px;
	height: 70px;
	background-image: url("../assets/port-milady.jpg");
	background-repeat: no-repeat;
	background-size: contain;
	background-position: center;
}
.group-item_banner-5 {
	width: 179px;
	height: 70px;
	background-image: url("../assets/port-ionet.jpg");
	background-repeat: no-repeat;
	background-size: contain;
	background-position: center;
}
.group-item_banner-6 {
	width: 179px;
	height: 70px;
	background-image: url("../assets/port-uxlink.jpg");
	background-repeat: no-repeat;
	background-size: contain;
	background-position: center;
}
.group-item_banner-7 {
	width: 179px;
	height: 70px;
	background-image: url("../assets/port-kava.jpg");
	background-repeat: no-repeat;
	background-size: contain;
	background-position: center;
}

.nova-partners_group > div {
	width: 220px;
	height: 95px;
	display: flex;
	justify-content: center;
	align-items: center;
	border-bottom: 1px solid rgba(216, 216, 216, 0.2);

	box-shadow: 0 0 30px 1px rgba(255, 255, 255, 0.1); /* 外部渐变光晕 */
	border: 2px solid transparent;
	background-origin: border-box;
	background-clip: padding-box, border-box;
}

.nova-form {
	margin-top: 40px;
	margin-bottom: 40px;
	text-align: center;
	color: #fff;
	width: 100%;
	height: 763px;
	background-image: url("../assets/form-bg.jpg");
	background-repeat: no-repeat;
	background-size: contain;
	position: relative;
}

.nova-form_title {
	margin-bottom: 0px;
	font-size: 42px;
}
.nova-form_title > p {
	font-weight: 400;
	line-height: 48px;
}

.twitter-logo {
	max-width: 52px;
	width: 52px;
	margin: 0 auto;
	margin-top: 20px;
	cursor: pointer;
}

.nova-form_container {
	width: 900px;
	height: auto;
	background: #09041f;
	background: linear-gradient(to top, #944efc, #09041f);
	margin: 30px auto 0;
	border-radius: 20px;
	padding: 40px 30px;
	box-shadow: 0 0 15px rgba(0, 0, 0, 0.3);
}

.nova-form_container-form {
	display: flex;
	flex-direction: column;
}

.form-row {
	display: flex;
	justify-content: space-between;
	margin-bottom: 20px;
}

.form-group {
	flex: 1;
	margin-right: 20px;
}

.form-group:last-child {
	margin-right: 0;
}

.form-group label {
	display: block;
	margin-bottom: 5px;
	color: #ccc;
}

.form-group input {
	width: 100%;
	height: 50px;
	padding: 10px;
	background-color: rgba(24, 24, 40, 0.3);
	border: none;
	border-radius: 10px;
	color: #fff;
}

textarea {
	width: 100%;
	height: 170px;
	padding: 10px;
	background-color: rgba(24, 24, 40, 0.3);
	border: none;
	border-radius: 10px;
	color: #fff;
	resize: none;
}

.word-count {
	text-align: right;
	color: #888;
	font-size: 12px;
	margin-top: 5px;
}

.button-row {
	text-align: center;
	/* margin-top: 20px; */
	margin: 0 auto;
}

.submit-button {
	background: #222;
	border: none;
	padding: 15px 30px;
	border-radius: 50px;
	color: white;
	font-size: 14px;
	cursor: pointer;
	box-shadow: 0 4px 15px rgba(0, 0, 0, 0.2);
	transition: all 0.3s ease;
}

.submit-button:hover {
	box-shadow: 0 4px 20px rgba(0, 0, 0, 0.4);
	transform: translateY(-3px);
}

.full-width {
	flex-direction: column;
}

.service1 {
	width: 48px;
	height: 48px;
	background-image: url("../assets/service1.jpg");
	margin-bottom: 20px;
}
.service2 {
	width: 48px;
	height: 48px;
	background-image: url("../assets/service2.jpg");
	margin-bottom: 20px;
}
.service3 {
	width: 48px;
	height: 48px;
	background-image: url("../assets/service3.jpg");
	margin-bottom: 20px;
}
.service4 {
	width: 48px;
	height: 48px;
	background-image: url("../assets/service4.jpg");
	margin-bottom: 20px;
}
.nova-footer {
	padding: 80px 160px 20px;
	box-sizing: border-box;
	display: flex;
}
.nova-footer_contact {
	width: 35%;
}
.nova-footer_contact-title {
	width: 85px;
	height: 30px;
	background-image: url("../assets/banner.jpg");
	background-repeat: no-repeat;
	background-size: contain;
}
.nova-footer_contact-detail {
}
.nova-footer_link {
	width: 65%;
	display: flex;
	justify-content: space-between;
}
.footer-link_item-title {
	font-size: 17px;
	color: #fff;
	font-weight: 500;
	margin-bottom: 20px;
}
.footer-link_item-link {
	font-size: 16px;
	margin-bottom: 20px;
	color: #888;
}
.nova-footer_contact-detail {
	display: flex;
	margin-top: 20px;
	margin-left: -5px;
}
.contact-detail_item {
	width: 30px;
	height: 30px;
	margin-right: 10px;
	/* background: #944efc; */
	border: 1px solid #944efc;
	border-radius: 30px;
	font-size: 15px;
	color: #d8d8d8;
	cursor: pointer;
	background-color: #020014; /* 背景色是渐变的起始色 */
	box-shadow: 0 0 5px 2px #944efc inset; /* 渐变效果：从外到内 */
	transition: box-shadow 0.3s ease; /* 平滑过渡效果 */

	background-repeat: no-repeat;
	background-position: center;
}
.contact-detail_item.twitter {
	background-image: url(../assets/icon-twitter.jpg);
	background-size: 10px;
}
.contact-detail_item.youtube {
	background-image: url(../assets/icon-youtube.jpg);
	background-size: 12px;
}
.contact-detail_item.telegram {
	background-image: url(../assets/icon-telegram.jpg);
	background-size: 12px;
}
.contact-detail_item.ins {
	background-image: url(../assets/icon-ins.jpg);
	background-size: 12px;
}
.copyright {
	width: 100%;
	text-align: center;
	padding: 10px 0;
}
.copyright > span {
	cursor: pointer;
}
</style>
