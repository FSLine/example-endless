<template>
	<v-row class="loop-container pa-0 ma-0">
        <v-col class="loop-page pa-0 ma-0" v-for="p in count" :key="p">
	        <slot></slot>
        </v-col>
	</v-row>
</template>


<script>
export default {
    data() {
        return {count:1}
    },

    mounted() {
        const vm = this;
        vm.$el.addEventListener('scroll', (event) => {
			vm.scrollHandler();
		}, true);

        const container = this.$el;
        if (container.scrollHeight >= container.childNodes[0].offsetHeight) {
            this.count+=1;
        }

    },

    methods: {

	    scrollHandler() {

            const container = this.$el;
            const page = container.childNodes[0]

            if (container.offsetHeight + container.scrollTop >= container.scrollHeight ) {
                this.count+=1
            }

            if (container.scrollTop > page.clientHeight) {
                container.scrollTop -= page.clientHeight
            }

        }

    }
}
</script>

<style>
.loop-container > .loop-page {
	min-width: 100%;
	flex-grow: 0;
}

.loop-container {
	display: flex;
	flex-direction: column;
	flex-wrap: nowrap;
	align-items: none;
	justify-content: flex-start;
	position: absolute;
	top: 0px;
	bottom: 0px;
	left: 0px;
	right: 0px;
	overflow-y: scroll;
	-webkit-overflow-scrolling: touch;
    -ms-overflow-style: none;  /* IE and Edge */
    scrollbar-width: none;  /* Firefox */
}

.loop-container::-webkit-scrollbar {
  display: none;
}



</style>
