<script lang="ts">
	export let companyName = 'Amazing Company, Inc.';
	export let additionalClasses = '';

	const sectionClasses = `w-full bg-white ${additionalClasses}`;
</script>

<section class={sectionClasses}>
	<div class="px-8 py-12 mx-auto max-w-7xl">
		<div class="grid grid-cols-12 gap-3 gap-y-8 md:gap-10 mb-3 lg:gap-20">
			<div class="col-span-12 md:col-span-3">
				<slot name="lhs" />
			</div>
			<nav class="col-span-12 sm:col-span-4 md:col-span-3 grid gap-y-3">
				<slot name="col1">
					<p class="font-semibold tracking-wider text-gray-400 uppercase">Product</p>
					<a href="/product/features" class="hover:text-black">Features</a>
					<a href="/product/documentation" class="hover:text-black">Documentation</a>
					<a href="/product/faq" class="hover:text-black">FAQs</a>
					<a href="/product/pricing" class="hover:text-black">Pricing</a>
				</slot>
			</nav>
			<nav class="col-span-12 sm:col-span-4 md:col-span-3 grid gap-y-3">
				<slot name="col2">
					<p class="font-semibold tracking-wider text-gray-400 uppercase">About Us</p>
					<a href="/about/story" class="hover:text-black">Our Story</a>
					<a href="/about/whoweare" class="hover:text-black">Our Employees</a>
					<a href="/about/impressum" class="hover:text-black">Company</a>
					<a href="/about/gdpr" class="hover:text-black">GDPR</a>
				</slot>
			</nav>
			<nav class="col-span-12 sm:col-span-4 md:col-span-3 grid gap-y-3">
				<slot name="col3">
					<p class="font-semibold tracking-wider text-gray-400 uppercase">Contact Us</p>
					<a href="/contact/support" class="hover:text-black">Support</a>
					<a href="/contact/press" class="hover:text-black">Press</a>
					<a href="/contact/email" class="hover:text-black">Email</a>
					<a href="/contact/jobs" class="hover:text-black">Jobs</a>
				</slot>
			</nav>
		</div>
		<div class="flex flex-col items-start justify-between pt-10 mt-10 border-t border-gray-100 md:flex-row md:items-center">
			<p class="mb-6 text-sm text-left md:mb-0">
				<slot name="copyright">© Copyright 2021 {companyName}. All Rights Reserved.</slot>
			</p>
			<div class="flex items-start justify-start space-x-6 md:items-center md:justify-center">
				<slot name="ToS">
					<a href="/legal/termsAndConditions" class="text-gray-600 hover:text-black">Terms</a>
					<a href="/legal/privacyPolicy" class="text-gray-600 hover:text-black">Privacy</a>
				</slot>
			</div>
		</div>
	</div>
</section>
