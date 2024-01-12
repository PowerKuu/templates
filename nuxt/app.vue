<script setup lang="ts">

</script>

<template>
	<SystemTopnav>
		<template #left>
			<SystemLogo/>
		</template>

		<template #right>
			<SystemFlex class="desktop" align="center" gap="1.5rem">
				<NavItems></NavItems>
			</SystemFlex>

			<SystemFlex class="mobile">
				<SystemHamburger class="mobile">
					<NavItems></NavItems>
				</SystemHamburger>
			</SystemFlex>	
		</template>
	</SystemTopnav>
	
	
	<NuxtLayout>
		<SystemFlex class="page">
			<NuxtPage/>
		</SystemFlex>
	</NuxtLayout>
</template>

<style scoped lang="scss">
.mobile {
	display: none !important;
}

@media screen and (max-width: 800px) {
	.desktop {
		display: none !important;
	}

	.mobile {
		display: flex !important;
	}
}
</style>

<style lang="scss">
@import url("https://fonts.googleapis.com/css2?family=Roboto:wght@200;300;400;500;600&display=swap");
@import url("https://fonts.googleapis.com/css2?family=Lato:wght@200;300;400;500;600&display=swap");
@import url("https://fonts.googleapis.com/css2?family=Figtree:wght@200;300;400;500;600&display=swap");

:root {
	--primary: #3563E9;
	--secondary: #161A34;
	--background: #ffffff;
	--neutral: #F1F1F4;
	--text: #575A6B;

	--page-padding: 3rem;
	
	--normal-height: 2.75rem;
	--border-radius: 10px;

	--border-width: 2px;
}

body {
	overflow-x: hidden;
}

* {
	font-family: "Figtree", sans-serif;
	font-weight: 500;

	margin: 0;
	padding: 0;
	box-sizing: border-box;
}

.page {
	padding-top: 8rem;
}

.text-overflow {
	overflow: hidden;
	text-overflow: ellipsis;
	white-space: nowrap;
}

a {
	text-decoration: none;
}
</style>