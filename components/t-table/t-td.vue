<template>
	<view class="t-td" :style="{ 'border-width': thBorder + 'rpx','border-color':borderColor ,'font-size':fontSize+'rpx' ,'color':color,'justify-content':tdAlignCpd, 'padding': padding}">
		<slot></slot>
	</view>
</template>

<script>
	export default {
		props: {
			align: String,
			padding: {
				type: String,
				default: '8rpx 14rpx'
			},
			color: {
				type: String,
				default: '#000'
			}
		},
		data() {
			return {
				thBorder: '1',
				borderColor: '#F9E4E4',
				fontSize: '14',
				tdAlign: 'center'
			};
		},
		inject: ['table', 'tr'],

		created() {
			this.thBorder = this.table.border;
			this.borderColor = this.table.borderColor;
			this.fontSize = this.tr.fontSize;
			if (this.align) {
				this.tdAlign = this.align;
			} else {
				this.tdAlign = this.tr.align
			}
		},
		computed: {
			tdAlignCpd() {
				let nameAlign = '';
				switch (this.tdAlign) {
					case 'left':
						nameAlign = 'flex-start'
						break;
					case 'center':
						nameAlign = 'center'
						break;
					case 'right':
						nameAlign = 'flex-end'
						break;
					default:
						nameAlign = 'center'
						break;
				}
				return nameAlign
			}
		}
	};
</script>

<style>
	.t-td {
		flex: 1;
		display: flex;
		align-items: center;
		width: 100%;
		border-top: 1rpx #d0dee5 solid;
		border-left: 1rpx #d0dee5 solid;
		text-align: center;
		color: #555c60;
		font-size: 28rpx;

	}
</style>
