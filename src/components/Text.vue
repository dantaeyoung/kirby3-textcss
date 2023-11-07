<template>
	<div class="textcss">
		<div :class="content.css">
		<component
		:is="component"
		ref="input"
		v-bind="textField"
		:value="content.text"
		class="k-block-type-text-input"
	
		@input="update({ text: $event })"
	/>
		</div>
		<div class="css_classes">
			<k-input
			ref="input"
			:value="content.css"
			class="class_input"
			type="text"
			@input="update({ css: $event })"
		/>
		</div>
	</div>
</template>

<script>
export default {
	computed: {
		component() {
			const component = "k-" + this.textField.type + "-input";

			if (this.$helper.isComponent(component)) {
				return component;
			}

			// fallback to writer
			return "k-writer";
		},
		placeholder() {
			return this.field("text", {}).placeholder;
		},
		textField() {
			return this.field("text", {});
		}
	},
	methods: {
		focus() {
			this.$refs.input.focus();
		}
	}
};
</script>

<style>

.textcss {
	display: flex;
}

.k-block-type-text-input {
	font-size: var(--text-base);
	line-height: 1.5em;
	height: 100%;
}
.k-block-type-text,
.k-block-container-type-text,
.k-block-type-text .k-writer .ProseMirror {
	height: 100%;
}
.css_classes {
    position: absolute;
    border: 1px dotted #caddfa;
    /* width: 100px !important; */
    font-size: 0.8em;
    /* text-align: right; */
    color: #62a6f1;
    /* font-family: 'Courier New', Courier, monospace; */
    /* font-style: italic; */
    /* margin-bottom: 2px; */
    min-width: 200px;
    /* overflow-wrap: anywhere; */
    top: 0px;
    left: 0px;
    padding: 3px 5px;
    opacity: 0.6;
	}

</style>
