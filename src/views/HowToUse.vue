<template>
    <div class="how-to-use">
        <vue-headful :title="$t('how-to-use.meta-title')" :description="$t('how-to-use.meta-description')"/>

        <section class="hero is-light">
            <div class="hero-body">
                <div class="container">
                    <h1 class="title is-size-3 has-text-centered is-unselectable">{{ $t('how-to-use.title') }}</h1>
                    <p class="subtitle has-text-centered has-text-grey is-unselectable">{{ $t('how-to-use.subtitle') }}</p>
                </div>
            </div>
        </section>

        <section class="hero">
            <div class="hero-body">
                <div class="container">
                    <div v-for="(item, i) in usageImages" :key="i">
                        <div class="columns is-mobile has-text-centered is-centered">
                            <div class="column is-narrow">
                                <figure class="has-captions">
                                    <ResponsiveImage class="image" :width="item.width" :height="item.height" :src="item.src" skeleton/>

                                    <figcaption v-html="$t(item.sub)"/>
                                </figure>
                            </div>
                        </div>
                    </div>

                    <p class="has-text-centered">
                        <a href="https://github.com/NickeManarin/ScreenToGif/wiki" target="_blank" rel="noopener"
                            @click="$gtag.event('How-to-use', {'event_category': 'Clicks', 'event_label': 'See more'})">
                            {{ $t('how-to-use.more') }}
                        </a>
                    </p>
                </div>
            </div>
        </section>
    </div>
</template>

<script>
    import ResponsiveImage from "@/components/ResponsiveImage.vue";

    export default {
        components: {
            ResponsiveImage
        },

        data() {
            return {
                usageImages: [
                    { src: require('@/assets/media/usage/1-Startup.png'), width: "486px", height: "213px", sub: "how-to-use.list.startup" },
                    { src: require('@/assets/media/usage/2-Recording.gif'), width: "587px", height: "401px", sub: "how-to-use.list.record" },
                    { src: require('@/assets/media/usage/3-Editor-Removing-Frames.gif'), width: "742px", height: "649px", sub: "how-to-use.list.edit-remove" },
                    { src: require('@/assets/media/usage/4-Editor-Adding-Transition.gif'), width: "742px", height: "649px", sub: "how-to-use.list.edit-transition" },
                    { src: require('@/assets/media/usage/5-Editor-Saving.gif'), width: "742px", height: "649px", sub: "how-to-use.list.edit-save" },
                    { src: require('@/assets/media/usage/6-Final-Gif.gif'), width: "544px", height: "362px", sub: "how-to-use.list.final-gif" },
                ]
            }
        }
    };
</script>

<style lang="scss">
    @import "@/mixins/colors.scss";

    //Background of the hero panel.
    // .hero.is-screenshots {
    //     background-image: linear-gradient($screenshots, $screenshots-light);
    // }

    //Makes the figure captions resize to the image.
    .has-captions {
        display: table;
    }

    figcaption {
        max-width: 100%;
        width: auto;
        display: table-caption;
        caption-side: bottom;
        background: white;
        margin: 0.25rem 0 1rem 0;
        border-radius: 5px;
    }
</style>