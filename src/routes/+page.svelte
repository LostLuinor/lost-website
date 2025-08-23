<script>
    import MainSection from '$lib/sections/MainSection.svelte';
    import AboutSection from '$lib/sections/AboutSection.svelte';
    import TimelineSection from '$lib/sections/TimelineSection.svelte';
    import WorksSection from '$lib/sections/WorksSection.svelte';
    import ContactSection from '$lib/sections/ContactSection.svelte';
</script>

<MainSection />
<div class="section-divider"></div>
<AboutSection />
<div class="section-divider"></div>
<TimelineSection />
<div class="section-divider"></div>
<WorksSection />
<div class="section-divider"></div>
<ContactSection />

<style>
    .section-divider {
        width: 100%;
        height: 2px;
        background: linear-gradient(to right, transparent, #475569, transparent);
        margin: 2rem 0;
        opacity: 0.6;
    }
</style>

